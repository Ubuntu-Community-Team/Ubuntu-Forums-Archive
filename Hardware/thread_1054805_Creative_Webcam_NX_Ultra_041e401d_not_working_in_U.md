---
title: "Creative Webcam NX Ultra 041e:401d not working in Ubuntu 8.10"
date: 2009-01-30
forum: Hardware
---

### Post by Anonymoose on 2009-01-30
I've installed the gspca drivers through Synaptic, updated libvl2 and all the libjasper packages if that means anything, but I can't get this webcam to work properly. After using the LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so workaround, I can get it to show image in camorama, but not cheese (I get the error: libv4l2: error dequeuing buf: Input/output error), but in camorama, the image I get is very dark and the colors are all wrong. Also, when I do use that workaround in camorama, I get this message: 

(camorama:6387): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated
 

Does anyone know anything that could help?

---

### Post by Anonymoose on 2009-01-30
I turned the brightness all the way up and added the color correction filter, and this helped things some, but everything is still very yellow and orange. Not at all what it should be. Does anyone know a way to possibly fix this, or is this the best I'm gonna get? :(

---

### Post by IceBadger on 2009-03-29
I am having the same issues with the same web camera.  The thing that rubs me is that I am pretty sure this camera worked pre-Ibex.  I could not get it to work in 8.10 or 9.04 beta.  I hate then usability regresses.

If I do get it working I will let you know.  Have you found a solution yet?

---

### Post by williamleest on 2009-07-10
You might need some software to view the webcam, like cheese.  At least worth a try out.

This site is for checking your webcam belongs to which driver it needed. 
For NX Ultra it's spca5xx

[http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html)

Otherwise you can go to creativelabs for their open source to check on the webcam you have and download drivers for your required webcam.  Which will still lead to the above.

[http://connect.creativelabs.com/opensource/Lists/Webcams/AllItems.aspx](http://connect.creativelabs.com/opensource/Lists/Webcams/AllItems.aspx)

Next you can install spca5xx manually

[https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)

---

