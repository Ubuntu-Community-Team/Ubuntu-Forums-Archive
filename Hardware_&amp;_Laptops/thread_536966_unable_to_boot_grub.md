---
title: "unable to boot grub"
date: 2007-08-28
forum: Hardware &amp; Laptops
---

### Post by markthien on 2007-08-28
Hi guys,

   I have just installed ubuntu 7.04 with existing windows xp. However, it failed to boot and hang at GRUB loader there. However, when I hook up my usb cd-rom to my laptop, then everything is fine. 

   Give me a break, I don't need the usb cd-rom everytime. pls help.

Mark

---

### Post by markthien on 2007-08-28
what I got is the following exception:

GRUB loading stage1.5

GRUB loading, please wait...
Error 25

I installed ubuntu in a usb 2.0 hdd. i am using HP Compaq nc4010 laptop.
when i restart it, it will be ok sometimes. 

please help.

---

### Post by uclalinux on 2007-08-29
please post your menu.lst  file in the /boot/grub

---

### Post by MrCheese on 2007-08-29
I'm guessing that it set up your hdd as second boot device - you can interrupt grub & edit the boot command (just follow the prompt at the bottom of the screen). Change the hdd device from (I'd guess) (1,x) to (0, x) where x is the partition no. Once edited, hit B for boot & your system should start up.

---

### Post by markthien on 2007-08-29
i have to turn on and off a few times then I can get into the menu which let me select ubuntu or windows xp. please help ..... help ....

---

### Post by strabes on 2007-08-29
This question has been asked many times. [http://ubuntuforums.org/showthread.php?t=117271](http://ubuntuforums.org/showthread.php?t=117271)

---

