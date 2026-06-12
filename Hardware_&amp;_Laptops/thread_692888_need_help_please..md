---
title: "need help please."
date: 2008-02-10
forum: Hardware &amp; Laptops
---

### Post by Krafturinn on 2008-02-10
I am trying to get my creative webcam do work. It is this type 

[http://is.europe.creative.com/products/product.asp?category=218&sub](http://is.europe.creative.com/products/product.asp?category=218&sub)
category=219&product=16959

they don't have linux driver so I am pretty much annoyed that my webcam doesn't work with ubuntu but I was wondering if you people could help me out get it to work.

When I checked to see if it was connected, I got this message, so the webcam is working in the usb port but how do I get it to work as a webcam ???

emil@Bulldog:~$ lsusb
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 041e:4052 Creative Technology, Ltd 
Bus 001 Device 003: ID 046d:c01e Logitech, Inc. MX518 Optical Mouse
Bus 001 Device 001: ID 0000:0000  


If you guys/girls can help out with this I would be very very grateful :) 

Best regards from Iceland

Emil

---

### Post by EXCiD3 on 2008-02-12
What software are you wanting to use your webcam with? To test to see if your webcam works with the built-in drivers open Ekiga Softphone from the Applications->Internet menu and try using the different drivers. Most webcams will run best (if at all) on the V4L2 driver. My HP webcam that came with my laptop works out of the box on the V4L2 driver. Good luck!

---

### Post by teeleef on 2008-02-12
Excid,  did you manage to get the built in HP microphone working at all?  Skype spots my webcam, but  I think the microphone is still suspect.


T

---

