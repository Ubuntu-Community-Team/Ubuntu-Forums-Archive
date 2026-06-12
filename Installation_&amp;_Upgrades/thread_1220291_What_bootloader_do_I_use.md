---
title: "What bootloader do I use?"
date: 2009-07-22
forum: Installation &amp; Upgrades
---

### Post by Theory5 on 2009-07-22
I am dual-booting ubuntu and vista. After I install ubuntu, I have no idea how i am going to get it to boot without keeping my usb flash drive connected. What bootloader should I use, what are my options?

---

### Post by raymondh on 2009-07-22
> **Theory5 said:**
> I am dual-booting ubuntu and vista. After I install ubuntu, I have no idea how i am going to get it to boot without keeping my usb flash drive connected. What bootloader should I use, what are my options?

Can you post the terminal output of

```
sudo fdisk -l
```

Your GRUB (the default bootloader for Ubuntu ... which when you installed Ubuntu overwrote the windows bootloader) could be in the USB thumb drive.
  
You'll need to install GRUB to the MBR.  Here's a  detailed and simple tutorial to follow:

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Good luck.  Back-up your files.

---

### Post by imtheguru on 2009-07-22
> **Theory5 said:**
> I am dual-booting ubuntu and vista. After I install ubuntu, I have no idea how i am going to get it to boot without keeping my usb flash drive connected. What bootloader should I use, what are my options?Perform a Wubi install of Ubuntu.

This is by far the most painless way to exercise a dual-boot system and keeps NT-Bootloader as the default bootloader.

Cheers.

---

### Post by starcannon on 2009-07-22
[U][Dual Boot Vista and Ubuntu How To]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

[/U]

---

### Post by stlsaint on 2009-07-22
after ubuntu is completely and successfully installed it should automatically boot into itself without the usb...you may want to recheck your installation if you have to boot thru usb everytime! and it should add itself to your vista booloader so you have the option to choose ubuntu...at least thats how it was for me!!

---

### Post by presence1960 on 2009-07-22
> **Theory5 said:**
> I am dual-booting ubuntu and vista. After I install ubuntu, I have no idea how i am going to get it to boot without keeping my usb flash drive connected. What bootloader should I use, what are my options?

How did you install Ubuntu? a Cd or a usb drive? Where did you install Ubuntu? to an internal hard disk or an external drive? more info is needed. be precise.

---

