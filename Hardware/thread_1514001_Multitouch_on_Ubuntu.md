---
title: "Multitouch on Ubuntu?"
date: 2010-06-20
forum: Hardware
---

### Post by NigelLane on 2010-06-20
Hi. :)

I have HP TouchSmart tx2, and with Ubuntu LucidLynx, and Dual Boot with Windows 7. :D

I really don't like Windows, but I find it a necessity, because most people use Windows ( although its really not good. ) The only reason I still spend some time on the Win7 is because it supports Multitouch.

I don't really know if there is such a thing on Ubuntu, but it's worth a try. I read something that mutitouch still isn't here but it is in progress... 

Can someone give me an update or something. Idk, maybe there is a way I can enable this? Help?

---

### Post by Favux on 2010-06-20
Hi NigelLane,

See the [N-trig HOW TO]("http://ubuntuforums.org/showpost.php?p=7863677&postcount=1").  Use Rafi's latest hid-ntrig.ko along with the latest firmware recommended.  You can use Ayuthia's python installer.  All highlighted in blue.

Then you'll have to configure.  That will depend on whether you want to try linuxwacom for 2FG (2 finger gestures) or evdev for touch (still use linuxwacom for the stylus).  Right now Rafi recommends evdev for multitouch.

---

