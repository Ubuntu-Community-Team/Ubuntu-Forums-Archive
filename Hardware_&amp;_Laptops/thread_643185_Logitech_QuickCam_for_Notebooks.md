---
title: "Logitech QuickCam for Notebooks"
date: 2007-12-17
forum: Hardware &amp; Laptops
---

### Post by Ertai87 on 2007-12-17
Hey guys!  So I'm switching to Ubuntu from not-quite-win-dows in the next couple days, and I've found that most of my hardware works, except for my webcam.  It's not that critical since apparently Pidgeon doesn't support webcam, but it would be nice to have anyway.  So basically, I want to know if anyone has had any luck in using it.  Unfortunately, Logitech came up with the great *AWESOME* idea of making 3 products with the EXACT SAME NAME, so it's impossible to find support for the one I have.  Here's a link to Logitech's software support page for my camera (includes a picture of the camera for reference):

[http://www.logitech.com/index.cfm/435/219&cl=ca,en](http://www.logitech.com/index.cfm/435/219&cl=ca,en)

Thanks for any help you can give me, and I apologize to the mods if this question has been answered already.

---

### Post by ragestar on 2007-12-17
da cam is working perfektly with ubuntu 7.10 and Samsung Q35!

---

### Post by linuxwizard on 2007-12-17
Plugin the webcam > than in terminal > To obtain the Vendor and Product ID's for USB devices, you can use: cat /proc/bus/usb/devices   And/Or   lsusb -v

Once you have Product & Vendor ID look in these two links using that info to find your webcam. That cam should work just need to figure out which driver you need. 
[http://www.quickcamteam.net/hcl/linux/logitech-webcams](http://www.quickcamteam.net/hcl/linux/logitech-webcams)
[http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html)

[https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)

[https://wiki.ubuntu.com/SkypeWebCams](https://wiki.ubuntu.com/SkypeWebCams)

---

