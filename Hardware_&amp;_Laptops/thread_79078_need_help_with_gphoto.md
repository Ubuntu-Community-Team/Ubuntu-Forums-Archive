---
title: "need help with gphoto"
date: 2005-10-19
forum: Hardware &amp; Laptops
---

### Post by skelooth on 2005-10-19
I'm really confused what to do and very frustrated. There are no digital
cameras in the local stores that work with gphoto, so I bought this Kodak
Easy Share CX4200 refurbished online.

When I plug it in to the USB port it brings up a dialog asking me if I'd
to import photos. If I say yes, it tells me no camera was detected. I can
manually select CX4200, but it won't allow me to select a port (ports list
comes up blank)

I have the same problem when running it from the command line

gphoto2 -P

*** Error ***
Could not detect any camera
*** Error (-105: 'Unknown model') ***

Please advise me what to do. I've already bought and returned one camera,
I really don't want to have to return this one via mail. I just need a
camera to work.

(all of my other usb devices work fine, I'm running Ubuntu Hoary Hedgehog
with the latest distro of gphoto2-2)

---

### Post by John.Michael.Kane on 2005-10-19
Try to see if your issue can be fixed here [http://www.gphoto.org/doc/manual/](http://www.gphoto.org/doc/manual/)
[http://www.gphoto.org/doc/manual/FAQ.html](http://www.gphoto.org/doc/manual/FAQ.html)

---

### Post by skelooth on 2005-10-19
[QUOTE=SD-Plissken]Try to see if your issue can be fixed here [http://www.gphoto.org/doc/manual/](http://www.gphoto.org/doc/manual/)
[http://www.gphoto.org/doc/manual/FAQ.html](http://www.gphoto.org/doc/manual/FAQ.html)[/QUOTE]

that was the first place I tried, there is nothing that documents my specific problem. It's like a cross between two problems. I tried setting up a hotplug script and it didn't change the situation.

I tried the gphoto mailing list yesterday morning and all I've gotten from it is spam.

---

### Post by majikstreet on 2005-10-19
I'm not familiar with gphoto, but I use fspot for my photo needs :)

---

### Post by skelooth on 2005-10-20
does fspot allow you to import pictures off of a digital camera via usb cable??

---

### Post by skelooth on 2005-10-20
WOW never mind. I can not get fspot to compile... I've already downloaded ~50MB of dependencies (from libperl-xml to mono-devel ???? wtf?) Now it's complaining that pkg-config can't find libgnome-2.0 .............. ugh.

There's no help for me huh? The gphoto mailing list is DEAD.

---

### Post by john_c on 2005-10-20
I use an EasyShare CX7330 with gthumb and it works well.  I have gphoto2 installed and use GTHUMB - File - Import photos function.  When I plug mine in and turn it on it never shows as an icon on the screen - gthumb is the only way I have found to import the photos.

Your camera is listed under those supported by gphoto2 at the following:

[http://www.gphoto.org/proj/libgphoto2/support.php](http://www.gphoto.org/proj/libgphoto2/support.php)

It took a bit of effort to get it set up and I can't recall all the details.  Make sure your users are members of the plugdev group if they wish to access the camera.

Plug in the usb cord, turn on the camera and then go into gthumb, files and import photos - give it a bit of time as it does take a few seconds to detect the camera and begin to show the thumbnails.

Let me know if this works and if not I can try to find out what I have installed\modified to get it to work.

John_c

---

