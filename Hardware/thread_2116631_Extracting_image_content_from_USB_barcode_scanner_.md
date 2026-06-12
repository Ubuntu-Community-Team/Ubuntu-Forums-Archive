---
title: "Extracting image content from USB barcode scanner help."
date: 2013-02-16
forum: Hardware
---

### Post by Wrezz on 2013-02-16
Hello there, 
I am currently working on a project in which I am working towards using a laser barcode scanner as a camera.
For the time being, I have been looking into extracting images from optical mice, are the concepts the same? So far extracting the image data seems to be a little elusive, I was wondering if anyone has had any experience with barcode scanners and the software needed to work with them?

Currently I am using a type LS2600 cable USB barcode scanner.

Super beginner but very capable. Ive been working with arduino for the past year if that helps anyone.

I'd really like to hear from you guys.

---

### Post by joshnoth on 2013-03-11
Sorry, I am not sure I have understood your question very well. Could you be more specific with the "image content"? What image content are you trying to get with a USB barcode [[COLOR=#000000]scanner[/COLOR]]("http://www.barcodelib.com/csharp/barcode_reader_csharp.html")?

---

### Post by makaveil4202 on 2014-01-27
I have a [[COLOR=#000000]USB barcode scanner[/COLOR]]("http://www.keepautomation.com/products/usb_barcode_scanner/") and been using it for a while. But I just use it to extract info encoded in barcode images, not some other kind of images. So I have no idea if you can use the [[COLOR=#000000]barcode scanner[/COLOR]]("http://www.keepautomation.com/products/net_barcode_reader/") as a camera to extract images from optical mice.
Here I Googled how exactly a barcode scanner works, you might take a look and try with ur own thing. 
[FONT=tahoma,arial,helvetica,sans-serif][SIZE=2] Basically, there are 3 functional parts to the barcode scanner itself, the illumination system, the sensor / converter, and the decoder.[/SIZE][/FONT]
[FONT=tahoma,arial,helvetica,sans-serif][SIZE=2]Barcode scanners begin by illuminating the code with red light. The sensor of the barcode scanner detects the reflected light from the illumination system and generates an analog signal with varying voltage that represent the intensity (or lack of intensity) of the reflection. The converter changes the analog signal to a digital signal which is fed to the decoder. The decoder  interprets the digital signal, does that math required to confirm and  validate that the barcode is decipherable, converts it into ASCII text,  formats the text and sends it to the computer the scanner is attached  to.[/SIZE][/FONT]

---

### Post by macjone on 2014-03-11
> **Wrezz said:**
> Hello there, 
I am currently working on a project in which I am working towards using a laser [[COLOR=#272727]barcode scanner[/COLOR]]("http://www.rasteredge.com/how-to/vb-net-imaging/read-barcode-vb-net/") as a camera.
For the time being, I have been looking into [[COLOR=#272727]extracting images from optical mice[/COLOR]]("http://www.rasteredge.com/how-to/vb-net-imaging/ocr-sdk/"), are the concepts the same? So far [COLOR=#272727]extracting the image data[/COLOR] seems to be a little elusive, I was wondering if anyone has had any experience with barcode scanners and the software needed to work with them?

Currently I am using a type LS2600 cable USB barcode scanner.

Super beginner but very capable. Ive been working with arduino for the past year if that helps anyone.

I'd really like to hear from you guys.

well, you can simply use some OCR library to extract data from image, so why do you have to use barcode scanner anyway?;)

---

### Post by massonmilo on 2014-08-14
> well, you can simply use some OCR library to extract data from image, so why do you have to use [[COLOR=#000000]barcode scanner[/COLOR]]("http://www.pqscan.com/barcode-scanner/") anyway?:wink:
Extracting image with OCR tech? As i know, OCR technology can recognize information from image, but cannot help with [[COLOR=#000000]reading barcode[/COLOR]]("http://www.pqscan.com/read-barcode/qrcode.shtml") except for integrating with a barcode reader source. Am i right?

---

### Post by coldraven on 2014-08-14
AFAIK a USB barcode scanner is recognised just as a keyboard, it will enter text into fields and that's it.
If you want to experiment with a web-cam then install Zbar
```
sudo apt-get install zbar-tools
```

Then run
```
zbarcam
```

Maybe it is possible to capture the image at the moment that zbarcam outputs the scanned barcode data, if that is what you need.

---

