---
title: "changing OS order in GRUB dual-boot"
date: 2009-03-12
forum: Installation &amp; Upgrades
---

### Post by Mythology on 2009-03-12
Hi, I am about to *RE*install Ubuntu onto my laptop to dual boot with windows. I've done this before perfectly... no problems and was very happy with the OS.

But there was ONE inconvenience. That was the GRUB dual-boot window. I think it's great and everything, but I would rather the first OS on the list be Windows XP than Ubunutu, because that is what I need to use most of the times (unfortunately.)

Is there a way to change the order of the OSs listed? How would I go about doing that safely?

*note* Grub screen: [http://users.bigpond.net.au/hermanzone/p15.htm#Temporarily_Edit_the_GRUB_Menu]("http://users.bigpond.net.au/hermanzone/p15.htm#Temporarily_Edit_the_GRUB_Menu")

---

### Post by whoop on 2009-03-12
```

gksudo gedit

```
open /boot/grub/menu.lst

search for "default		0" etnry
Change the 0 to the value pointing to the grub line you want to boot default (o, is the first entry 1 the second etc.)

---

### Post by Mythology on 2009-03-12
Thank you. I will try that after I install in a short bit. (I'm running on Live CD now.) :KS

---

### Post by Mythology on 2009-03-13
I tried that and didn't get anywhere but I looked around on this forum and someone posted a link to a community help guide about this exact problem.

I fixed it! I got it to default boot XP and I even tried out changing the number of seconds until the OS boots.

Very cool.
Thanks for your effort though. You are a :KS

---

