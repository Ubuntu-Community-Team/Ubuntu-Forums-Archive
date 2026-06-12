---
title: "HELP!!! Laptop only gets me to BusyBox"
date: 2008-12-15
forum: Hardware
---

### Post by LiquidOC on 2008-12-15
I have tried the 8.04 livecd and the 7.04 livecd and still nothing other than busybox. I had 8.04 installed on an external hard drive, and rebooted, and dropped to busybox, figuring it was a problem with my xorg.conf file (I was mucking about in it) I decided to try and reboot with a livecd and edit it back to restore the original config. Well, now all livecd's are dropping me to a busybox as well. If I turn off quiet splash when I'm booting the livecd...I get errors when it tries to assign some type of number to the USB drives....could it be that my USB Controller is finally failing?

Thanks!!

---

### Post by tommcd on 2008-12-15
For troubleshooting purposes, unplug all usb devices from the laptop and see if you can boot the live CD.

---

### Post by LiquidOC on 2008-12-16
Ah, but therein lies the problem, this is a laptop, and I have no internal CD-ROM on it anymore, only an external one...the internal one no longer functions properly, and cannot read an image off of cd, it just spins the disk endlessly.

Thanks!

---

### Post by tommcd on 2008-12-17
Can you confirm that the live CDs work on another computer? Also, try booting something like a Gparted Live CD if you have one or you can burn one on another computer. If the live CDs all boot on another computer, and if you can't even boot a Gparted live CD on the laptop, then I might suspect a hardware problem with the laptop.

---

### Post by LiquidOC on 2008-12-17
The cd's do work in my work computer, and I did try the g-parted live cd. I'm actually going to give up on this old computer (this laptop is only 4 years old....I guess this is why you shouldn't spend 3000 bucks on an alienware....they crap out.) Anyways, I was planning on getting a netbook (probably the S10 from lenovo :) ) for the meantime. Thanks for all the help though, but the computer has already been thrown away.

Thanks!

---

### Post by tommcd on 2008-12-18
The Lenovo S10 has a Broadcom wireless chip, but according to this website everything works out of the box in Ubuntu 8.10:
[http://www.linlap.com/wiki/lenovo+ideapad+s10](http://www.linlap.com/wiki/lenovo+ideapad+s10)
The Acer Aspire One will also work:
[https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne)

Let me know how that Lenovo S10 turns out.

---

