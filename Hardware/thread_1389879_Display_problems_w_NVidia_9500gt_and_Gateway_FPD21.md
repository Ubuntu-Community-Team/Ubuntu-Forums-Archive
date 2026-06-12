---
title: "Display problems w/ NVidia 9500gt and Gateway FPD2185W"
date: 2010-01-24
forum: Hardware
---

### Post by t2k on 2010-01-24
I recently installed 9.10 x64 bit on my desktop computer. Installation was all succesful, no errors or anything. However once the computer was restarted the display resolution was wrong. I went to system> hardware devices, and it says the video driver is up to date. it is using the nvidia non-open source driver. The display is a Gateway FPD2185W, with a native resolution of 1680x1050. When I open the xserver settings, it only detects a generic crt and says the maximum possible resolution is 1280x768. Any ideas on how to get it to detect the monitor and allow me to run full resolution?

---

### Post by ScarySquirrel on 2010-02-21
This looks similar to this problem:
[http://ubuntuforums.org/showthread.php?t=1307848&highlight=nvidia+driver+resolution](http://ubuntuforums.org/showthread.php?t=1307848&highlight=nvidia+driver+resolution)

whose solution can be found at this link:
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

---

### Post by ScarySquirrel on 2010-04-24
[IMG]http://icanhascheezburger.files.wordpress.com/2009/06/funny-pictures-kitten-will-fix-it.jpg[/IMG]

Soo... did that link help at all? 
... 
Are you even there? 
Are you even real? 
Is any of this real? AAAAAAAAHHHHH BLUE PILL! BLUE PILL!

---

### Post by pi/roman on 2010-04-24
Your monitor may be able to do 1680x1050 but you could still be limited by your graphics adapter. I am assuming though since it is Nvidia that it has a fairly high resolution. Post your xorg.conf so we can see if anything is wrong with it.

---

