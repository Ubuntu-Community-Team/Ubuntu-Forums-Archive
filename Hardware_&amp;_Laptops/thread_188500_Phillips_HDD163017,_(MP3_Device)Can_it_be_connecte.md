---
title: "Phillips HDD1630/17, (MP3 Device)Can it be connected?"
date: 2006-06-04
forum: Hardware &amp; Laptops
---

### Post by rjcube on 2006-06-04
I have a MP3 player, it as a Philips HDD1630/17, and I wanted to know if it is possible to get it connected to ubuntu to play and/or transfer files?

---

### Post by givré on 2006-06-04
Try it, it should be recognise as an usb device.

---

### Post by rjcube on 2006-06-04
[QUOTE=givré]Try it, it should be recognise as an usb device.[/QUOTE]

I tried plugging it in already, nothing happined, I also looked in the device manager to see if i could find anything but nothing is there either.

---

### Post by givré on 2006-06-04
I found that about the subject [http://www.shahine.com/omar/CommentView,guid,c3a4a2c9-f6ec-4f5c-8ffe-0aba75359a2d.aspx](http://www.shahine.com/omar/CommentView,guid,c3a4a2c9-f6ec-4f5c-8ffe-0aba75359a2d.aspx)
(search for linux in the page) .
Unfortunatly it will probably not work at all. 

But the thing is you should see something in device manager even if it is not working. Do you have usb-storage enable? To check that see the output of ```
modprobe -l|grep usb-storage
``` if you get nothing enable it by ```
sudo modprobe usb-storage
```and try an other time.

---

### Post by rjcube on 2006-06-04
[QUOTE=givré]I found that about the subject [http://www.shahine.com/omar/CommentView,guid,c3a4a2c9-f6ec-4f5c-8ffe-0aba75359a2d.aspx](http://www.shahine.com/omar/CommentView,guid,c3a4a2c9-f6ec-4f5c-8ffe-0aba75359a2d.aspx)
(search for linux in the page) .
Unfortunatly it will probably not work at all. 

But the thing is you should see something in device manager even if it is not working. Do you have usb-storage enable? To check that see the output of ```
modprobe -l|grep usb-storage
``` if you get nothing enable it by ```
sudo modprobe usb-storage
```and try an other time.[/QUOTE]

USB and everything works fine, is there any possible way to emulate windows so the MP3 thinks its connecting to windows?

---

### Post by givré on 2006-06-04
The only way is to use vmplayer (wine will not work in this case) which will emulate completly wndows (yeh you will have to install a complete OS :cool: )

Try this how to [http://www.ubuntuforums.org/showthread.php?t=84275&highlight=vmplayer](http://www.ubuntuforums.org/showthread.php?t=84275&highlight=vmplayer)

---

### Post by swkiller on 2006-09-07
I know this topic has been dead for months, but what about [this]("http://ubuntuforums.org/showthread.php?t=135845") guide.  Philips hdd1630 seems to use MTP to transfer music, and I would guess if you could set it up with that guide then you should be able to use certian media players to transfer music such as amarok.

---

