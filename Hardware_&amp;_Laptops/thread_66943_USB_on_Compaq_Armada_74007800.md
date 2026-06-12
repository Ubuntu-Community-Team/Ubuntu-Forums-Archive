---
title: "USB on Compaq Armada 7400/7800"
date: 2005-09-18
forum: Hardware &amp; Laptops
---

### Post by mckemie on 2005-09-18
The USB on Compaq Armada 7400s & 7800s is not properly supported in kernels 2.6.x, but works fine in 2.4.2x.

I have installed a standard Debian 2.4.27 package on Hoary, but X fails to start.  Can anyone suggest what might be wrong?  Or point me to a 2.4.2x package that WILL work on Hoary?

---

### Post by mlomker on 2005-09-19
I did some Google searches and didn't turn up a whole lot, other than confirming your USB issue.  Compaq must have used a non-standard chipset implementation or something.  Not that long ago Compaq designed many of their own chips, so that might be the story.

What video driver are you using?  What errors are you seeing in /var/log/Xorg.0.log?  Have you already tried **dpkg-reconfigure xserver-xorg**?  Maybe try the VESA driver until you can figure out something better?

---

### Post by mckemie on 2005-09-20
Thanks for the suggestions!  I found that /var/log/Xorg.0.old (after a boot back to 2.6.10) tells me that /dev/input/mice did not exist on the 2.4.27 boot.  And apparently does exist under 2.6.10.

I recall seeing mention of "udev" or some such as a new feature of 2.6, but have no idea about it's use/significance.

Actually, the 2.4.27 problem is more sever than just X failing to start.  After X fails to start, the entire system is unresponsive.  No virtual consoles.

---

### Post by mlomker on 2005-09-20
> I recall seeing mention of "udev" or some such as a new feature of 2.6, but have no idea about it's use/significance.


Udev is a service that works in conjunction with HAL and Hotplug.  Basically it creates device entries in /dev dynamically depending upon what devices are detected.

---

### Post by mckemie on 2005-09-20
SO!  My fix may be as simple as changing in /etc/X11/Xorg.conf
         Option          "Device"                "/dev/input/mice"
to something like                               "/dev/psaux"
?
You reckon that would work on both 2.6.10 and 2.4.27?

---

### Post by mckemie on 2005-09-20
Some progess:
Changed "/dev/input/mice" to "/dev/psaux" and X seemed to work under 2.6.10.  Booted 2.4.27 and found that I needed to change "Protocol" "ImPS2" to "Protocol" "PS2".
BUT, a lot of stuff did not start: gnome-panel and other basic stuff.  I guess hotplug and/or HAL did not go since I could not mount a USB drive via a virtual console.

I guess what I really need is a "Installing 2.4 Kernels on Hoary systems" howto.  Hoary seems to be pretty tightly bound to 2.6.

Or get kernel developers to bring 2.6 up to 2.4 standards.

Or find my Libranet 2.8.1 CDs.

---

### Post by mlomker on 2005-09-21
> I guess what I really need is a "Installing 2.4 Kernels on Hoary systems" howto.  Hoary seems to be pretty tightly bound to 2.6.


Fighting progress is a difficult thing. You should be able to find a number of older distributions based on 2.4 kernels.  Linux needs to keep pushing forward to support new hardware because the competition is going to be Windows Vista and is currently the functionality that XP and OS-X provide.

Laptops start at $600 new and I just sold my old one for $400...Athlon XP 2400+ with the usual extras.  I don't think anyone is going to work on backporting to older hardware in light of the costs and market realities.

---

