---
title: "Creative Webcam Instant"
date: 2005-03-19
forum: Hardware &amp; Laptops
---

### Post by munki on 2005-03-19
Hi there peeps'

I own a little nice Webcam from Creative, but after I've changed to ubuntu Linux
I have been searching for a way to get it to work in Xorg.  ](*,) 

Anybody got any experience in that?

---

### Post by trash on 2005-03-19
I don't have the same cam, but to get my quick cam to work I downloaded the 'libpt-plugins-v4l' from universe/multi.

v4l2 is installed by default in Hoary, but it never works for me.

good luck.

edit
sorry just noticed you are Warty, this might be of no use to you... but i did have a similar problem in Warty and i might have posted what my fix was.

---

### Post by sunny on 2005-03-20
[QUOTE=munki]Hi there peeps'

I own a little nice Webcam from Creative, but after I've changed to ubuntu Linux
I have been searching for a way to get it to work in Xorg.  ](*,) 

Anybody got any experience in that?[/QUOTE]
 Check out the Webcam Howto at tldp [http://www.tldp.org/HOWTO/Webcam-HOWTO/](http://www.tldp.org/HOWTO/Webcam-HOWTO/)
Read the section on "Specific Webcam Models"  to find out which driver(module) supports your webcam and then go accordingly>> if the webcam is supported in the kernel or you have to compile/install the driver for your webcam.

---

