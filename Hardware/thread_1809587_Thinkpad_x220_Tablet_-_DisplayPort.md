---
title: "Thinkpad x220 Tablet - DisplayPort"
date: 2011-07-21
forum: Hardware
---

### Post by Kouran-sama on 2011-07-21
Hi, 
I'm using natty on my Thinkpad x220 Tablet (i7, intel 3000HD). 

I have a small problem: I can use my external monitor just fine when i use my VGA output, but when I connect it to the DisplayPort I only get a black screen with a mouse pointer on my notebook and the display itself says no signal. any idea how to troubleshoot?

Thanks
Tom

---

### Post by Kouran-sama on 2011-07-27
Updating to the linux kernel 3rc7 fixed the issue, however xf86-input-multitouch doesnt work with this one. so no tablet functionality.

---

### Post by Favux on 2011-07-27
Hi Kouran-sama,

xf86-input-wacom in the xserver-xorg-input-wacom package should support multitouch on the X220t as long as it is a least version 0.11.1.  What is the default version in Oneiric?

See the X220t thread:  [http://ubuntuforums.org/showthread.php?t=1785015](http://ubuntuforums.org/showthread.php?t=1785015)

---

