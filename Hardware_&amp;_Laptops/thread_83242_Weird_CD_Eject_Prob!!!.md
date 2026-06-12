---
title: "Weird CD Eject Prob!!!"
date: 2005-10-28
forum: Hardware &amp; Laptops
---

### Post by john_john on 2005-10-28
Hiya i got a Fujitsu Siemens Amilo L laptop and its got a strange prob ejecting CD's.  When there is no CD in the drive the button to open the tray works fine but when there is a CD in there and the tray is closed the button no longer works and the only way to eject it is to right click on it on the Desktop and select Eject.  Is This Normal???  I'm running Breezy if that helps.

Cheers

John

---

### Post by frodon on 2005-10-28
Yes this is normal, it's the ubuntu behaviour.

You might get errors like "device is busy" sometimes, it's because you have an opened application which use the CD (like nautilus).
To force CD eject use this command in a terminal : ```
sudo eject cdrom0
```
If you would like an icon on the panel to eject the CD/DVD and not get back to the desktop and right-clic on the CD-Rom icon : [http://ubuntuforums.org/showthread.php?t=52768&highlight=cd+eject](http://ubuntuforums.org/showthread.php?t=52768&highlight=cd+eject)

---

### Post by john_john on 2005-10-28
Thanks for that my minds at rest now

cheers

john

---

### Post by kreso on 2005-10-28
But is there a way to make the CD-rom unmount when the eject button is pressed? I mean, what the heck is it for then anyway?

---

### Post by jeffreyvergara.NET on 2005-10-28
try this.. 

> sudo sh -c 'echo "dev.cdrom.lock=0" >> /etc/sysctl.conf'

---

### Post by No6 on 2005-10-28
That works. :-)

Not that I'll be using it as I prefer to assign a keyboard shortcut to eject. Which works well for me. ;-)

---

### Post by kreso on 2005-10-28
Thanks a lot! You've solved one of my oldest linux problems :D

---

