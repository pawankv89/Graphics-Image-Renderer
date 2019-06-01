# Graphics Image Renderer

=========

## Graphics Image Renderer in Swift 5.

------------
Added Some screens here.

![](https://github.com/pawankv89/Graphics-Image-Renderer/blob/master/images/screen_1.png)
![](https://github.com/pawankv89/Graphics-Image-Renderer/blob/master/images/screen_2.png)
![](https://github.com/pawankv89/Graphics-Image-Renderer/blob/master/images/screen_3.png)
![](https://github.com/pawankv89/Graphics-Image-Renderer/blob/master/images/screen_4.png)
![](https://github.com/pawankv89/Graphics-Image-Renderer/blob/master/images/screen_5.png)
![](https://github.com/pawankv89/Graphics-Image-Renderer/blob/master/images/screen_6.png)
![](https://github.com/pawankv89/Graphics-Image-Renderer/blob/master/images/screen_7.png)

## Usage
------------

####  Graphics Image Renderer

```swift


import UIKit

class ViewController: UIViewController {

@IBOutlet weak var imageView: UIImageView!

override func viewDidLoad() {
super.viewDidLoad()
// Do any additional setup after loading the view.

//Graphics 1
//self.drowGraphics_1()

//Graphics 2
//self.drowGraphics_2()

//Graphics 3
//self.drowGraphics_3()

//Graphics 4
//self.drowGraphics_4()

//Graphics 5
//self.drowGraphics_5()

//Graphics 6
//self.drowGraphics_6()

//Graphics 7
self.drowGraphics_7()
}


//MARK: - Graphics 1
func drowGraphics_1() -> () {

if #available(iOS 10.0, *) {

if let img = UIImage(named: "screen_1"), let img2 = UIImage(named: "screen_2") {
let rect = CGRect(x: 0, y: 0, width: img.size.width, height: img.size.height)
let renderer = UIGraphicsImageRenderer(size: img.size)

let result = renderer.image { ctx in
// fill the background with white so that translucent colors get lighter
UIColor.white.set()
ctx.fill(rect)

img.draw(in: rect, blendMode: .normal, alpha: 1)
img2.draw(in: rect, blendMode: .luminosity, alpha: 1)
}

imageView.image = result
}


} else {
// Fallback on earlier versions
}
}

//MARK: - Graphics 2
func drowGraphics_2() -> () {

if #available(iOS 10.0, *) {

func addRainbow(to img: UIImage) -> UIImage {
// create a CGRect representing the full size of our input iamge
let rect = CGRect(x: 0, y: 0, width: img.size.width, height: img.size.height)

// figure out the height of one section (there are six)
let sectionHeight = img.size.height / 6

// set up the colors – these are based on my trial and error
let red = UIColor(red: 1, green: 0.5, blue: 0.5, alpha: 0.8)
let orange = UIColor(red: 1, green: 0.7, blue: 0.35, alpha: 0.8)
let yellow = UIColor(red: 1, green: 0.85, blue: 0.1, alpha: 0.65)
let green = UIColor(red: 0, green: 0.7, blue: 0.2, alpha: 0.5)
let blue = UIColor(red: 0, green: 0.35, blue: 0.7, alpha: 0.5)
let purple = UIColor(red: 0.3, green: 0, blue: 0.5, alpha: 0.6)
let colors = [red, orange, yellow, green, blue, purple]

let renderer = UIGraphicsImageRenderer(size: img.size)
let result = renderer.image { ctx in
UIColor.white.set()
ctx.fill(rect)

// loop through all six colors
for i in 0 ..< 6 {
let color = colors[i]

// figure out the rect for this section
let rect = CGRect(x: 0, y: CGFloat(i) * sectionHeight, width: rect.width, height: sectionHeight)

// draw it onto the context at the right place
color.set()
ctx.fill(rect)
}

// now draw our input image over using Luminosity mode, with a little bit of alpha to make it fainter
img.draw(in: rect, blendMode: .luminosity, alpha: 0.6)
}

return result
}

imageView.image = addRainbow(to: UIImage(named: "screen_1")!)


} else {
// Fallback on earlier versions
}
}

//MARK: - Graphics 3
func drowGraphics_3() -> () {

if #available(iOS 10.0, *) {

let renderer1 = UIGraphicsImageRenderer(size: CGSize(width: 500, height: 500))
let img1 = renderer1.image { ctx in
ctx.cgContext.setStrokeColor(UIColor.white.cgColor)
ctx.cgContext.setLineWidth(3)

ctx.cgContext.move(to: CGPoint(x: 50, y: 450))
ctx.cgContext.addLine(to: CGPoint(x: 250, y: 50))
ctx.cgContext.addLine(to: CGPoint(x: 450, y: 450))
ctx.cgContext.addLine(to: CGPoint(x: 50, y: 450))

let rectangle = CGRect(x: 0, y: 0, width: 512, height: 512)
ctx.cgContext.addRect(rectangle)
ctx.cgContext.drawPath(using: .fillStroke)

ctx.cgContext.closePath()
ctx.cgContext.strokePath()
}

imageView.image = img1

} else {
// Fallback on earlier versions
}
}

//MARK: - Graphics 4
func drowGraphics_4() -> () {

if #available(iOS 10.0, *) {

let renderer2 = UIGraphicsImageRenderer(size: CGSize(width: 512, height: 512))
let img2 = renderer2.image { ctx in
ctx.cgContext.setStrokeColor(UIColor.black.cgColor)

ctx.cgContext.translateBy(x: 256, y: 256)

var first = true
var length: CGFloat = 256

for _ in 0 ..< 256 {
ctx.cgContext.rotate(by: CGFloat.pi / 2)

if first {
ctx.cgContext.move(to: CGPoint(x: length, y: 50))
first = false
} else {
ctx.cgContext.addLine(to: CGPoint(x: length, y: 50))
}

length *= 0.99
}

//ctx.cgContext.closePath()
ctx.cgContext.strokePath()
}

imageView.image = img2

} else {
// Fallback on earlier versions
}
}

//MARK: - Graphics 5
func drowGraphics_5() -> () {

if #available(iOS 10.0, *) {

func drawLines() -> UIImage {
// 1
let renderer = UIGraphicsImageRenderer(size: CGSize(width: 280, height: 250))

let img = renderer.image { ctx in
// 2
ctx.cgContext.move(to: CGPoint(x: 20.0, y: 20.0))
ctx.cgContext.addLine(to: CGPoint(x: 260.0, y: 230.0))
ctx.cgContext.addLine(to: CGPoint(x: 100.0, y: 200.0))
ctx.cgContext.addLine(to: CGPoint(x: 20.0, y: 20.0))

ctx.cgContext.setLineWidth(10)
ctx.cgContext.setStrokeColor(UIColor.black.cgColor)

// 3
ctx.cgContext.strokePath()
}

return img
}

imageView.image = drawLines()

} else {
// Fallback on earlier versions
}
}

//MARK: - Graphics 6
func drowGraphics_6() -> () {

if #available(iOS 10.0, *) {

func drawRectangle() -> UIImage {
let renderer = UIGraphicsImageRenderer(size: CGSize(width: 280, height: 250))

let img = renderer.image { ctx in
let rectangle = CGRect(x: 0, y: 0, width: 280, height: 250)

// 4
ctx.cgContext.setFillColor(UIColor.yellow.cgColor)
ctx.cgContext.setStrokeColor(UIColor.gray.cgColor)
ctx.cgContext.setLineWidth(20)

// 5
ctx.cgContext.addRect(rectangle)
ctx.cgContext.drawPath(using: .fillStroke)
}

return img
}

imageView.image = drawRectangle()

} else {
// Fallback on earlier versions
}
}

//MARK: - Graphics 7
func drowGraphics_7() -> () {

if #available(iOS 10.0, *) {

func drawCircle() -> UIImage {
let renderer = UIGraphicsImageRenderer(size: CGSize(width: 250, height: 250))

let img = renderer.image { ctx in
let rect = CGRect(x: 5, y: 5, width: 240, height: 240)

// 6
ctx.cgContext.setFillColor(UIColor.blue.cgColor)
ctx.cgContext.setStrokeColor(UIColor.black.cgColor)
ctx.cgContext.setLineWidth(10)

ctx.cgContext.addEllipse(in: rect)
ctx.cgContext.drawPath(using: .fillStroke)
}

return img
}

imageView.image = drawCircle()

} else {
// Fallback on earlier versions
}
}


}



```




## License

This code is distributed under the terms and conditions of the [MIT license](LICENSE).

## Change-log

A brief summary of each this release can be found in the [CHANGELOG](CHANGELOG.mdown). 
