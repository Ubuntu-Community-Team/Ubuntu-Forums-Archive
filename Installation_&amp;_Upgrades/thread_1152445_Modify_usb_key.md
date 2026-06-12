---
title: "Modify usb key"
date: 2009-05-07
forum: Installation &amp; Upgrades
---

### Post by captkirk on 2009-05-07
I have a usb key I set up to run on a acer aspire one.  I used the canonical installation.  I would like to change some of the programs that are on the key when I boot from it.  Are there any instructions around to do remove some of the programs and add others?

---

### Post by pastalavista on 2009-05-07
I'm not sure what you mean by the "canonical installation". How did you make the USB bootable? Is it from an Ubunto iso?

---

### Post by captkirk on 2009-05-07
Sorry, I should have been more clear.  I used the instructions at [https://wiki.ubuntu.com/UNR](https://wiki.ubuntu.com/UNR)

I am using a bootable key.  The site I quoted has a modified img file to install to a bootable disk.  Everything works fine, but I want to change what is on the usb key.

Thanks for your help.

---

### Post by pastalavista on 2009-05-07
The UNR install only comes in .img format instead of .iso. The usb-creator program can mount an .iso to a USB and leave it open for changes (persistent installation). You can find a program that will convert an .img file to an .iso and then it could be installed with usb-creator which can't handle .img files.

---

