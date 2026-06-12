---
title: "Current Canon EOS sotware to run on Ubuntu"
date: 2016-12-09
forum: Hardware
---

### Post by Vaclav Vasek on 2016-12-09
I am after getting pictures from Canon EOS camera.  
A search recommended to use gimp, but I do not see any way to connect to camera using it. 
Did some more Googling and came up with ancient ( 2010 ) stuff. 
**Is there more recent software to connect Ubuntu to Canon EOS camera?**
I do not want to go back to anything MS ( VirtualBox . WINE etc). 
And I do not have means to read the SD directly. 

Any to the  subject reply would be appreciated and it I posted this in wrong place, just ignore it.

---

### Post by ajgreeny on 2016-12-09
Can you simply attach the camera as a mass storage device (like a USB drive) and then copy the files to your hard disk?

I can not see any reason why you would need gimp just to transfer pics; I always did it using the file-manager, though if you want a photo manager software have a look at gthumb.  I have no idea if that camera will work in that manner as a USB drive, but many do.

---

### Post by Vaclav Vasek on 2016-12-10
This is my first attempt to connect to Canon camera and I do not believe it it just simple "copy file " affair. 
Using lsusb does not help much - it only shows that Canon has a USB port attached. 

In the meantime I have found Shotwell which connects to Canon but has an issue. 
From my ears of experience working with multivendor / source software I'll will post my issue here and when I find where to post it to notify the aothors of the Shotwell I'll post it there. 

The issue is - the Showell app looses control of the USB port AFTER few hundred of photofiles are sucessuly loaded. 
Than is gets in initial mode and claims to start downlodaing fiels again but it does not. 

On Shotwell FAQ site this issue is discussed , here is the link
[http://gphoto.org/doc/manual/permissions-usb.html](http://gphoto.org/doc/manual/permissions-usb.html)

This link seem pretty old and does not specifically address Linux / Ubuntu but indicates that this "USB permission" is part of the kernel.

Needles to say - if the hardware can be accessed - the photos are initially downloaded - why the permission gets lost?

Since this issue with Shotwell I am still looking application to download my photos.

---

### Post by gordintoronto on 2016-12-10
As ajgreeny suggested, just use the file manager. Details depend on what version of Linux you are using, and perhaps which Canon camera you have.

Mark the files you want to copy, go to Pictures. and perhaps make and go to a folder such as 20161210, then paste the files into the folder.

---

### Post by cariboo on 2016-12-10
Have you tried digikam? It's a KDE app, so it pulls in quite a few extra dependencies. I personally find it works much better than shotwell.

---

