---
title: "External HD?"
date: 2010-02-21
forum: Hardware
---

### Post by DarthScape on 2010-02-21
Just a quick question all. I want to install Xubuntu 10.04 on my pc. Problem is, I absolutely hate dual-booting; I feel like grub contaminates my hard drive, no offense. So what I'm looking at is getting an external hard drive to install it to. There is no more room for another sata or e-sata drive in my computer (thanks to my 9800gtx). Will USB be fast enough to run ubuntu from, or is it even worth it? With that, what would be the fastest external drive? Also, with an external usb drive, would 7200 vs 5400 matter?

---

### Post by icyzer on 2010-02-22
> **DarthScape said:**
> Just a quick question all. I want to install Xubuntu 10.04 on my pc. Problem is, I absolutely hate dual-booting; I feel like grub contaminates my hard drive, no offense. So what I'm looking at is getting an external hard drive to install it to. There is no more room for another sata or e-sata drive in my computer (thanks to my 9800gtx). Will USB be fast enough to run ubuntu from, or is it even worth it? With that, what would be the fastest external drive? Also, with an external usb drive, would 7200 vs 5400 matter?
The speed of the OS is going to be limited to the hdd/usb speed. Best thing you could do is, as far as I know. Get a longer sata/e-sata cabel that goes outside your PC. That way you keep that speed.

---

### Post by tom4jean on 2010-02-28
You can make ubuntu dual bootable without touching your windows MBR at all. Read through this wiki post and especially the section about the Master Boot Record. 

You just have to run a small program called EasyBSD in windows , there is a link to it in the instructions on the page.

Also read through the instruction pages on the EasyBSD web site, they have a section on ubuntu specifically.
The most important part is that when you install ubuntu do not let it put GRUB on your MBR or it will take over the windows one.
It has to be installed to the partition with Ubuntu.

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

I used this to put ubuntu on a second internal hardrive without touching my windows drive at all other then adding the ubuntu entry into the windows mbr using the EasyBSD program.
It works great and more importantly kept my wife happy that I did not mess with the windows drive.
;)

---

### Post by sgosnell on 2010-02-28
You should be able to run Ubuntu from a USB HDD.  It's not that slow.  Just make absolutely sure you install the bootloader to the external drive, not to your internal HDD, or you won't be able to boot at all without having the external drive attached.

---

