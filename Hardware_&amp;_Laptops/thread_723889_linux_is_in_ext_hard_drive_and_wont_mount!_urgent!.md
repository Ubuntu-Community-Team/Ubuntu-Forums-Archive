---
title: "linux is in ext hard drive and wont mount! urgent!"
date: 2008-03-14
forum: Hardware &amp; Laptops
---

### Post by pontifex3 on 2008-03-14
hi, this post is extremely urgent! im giving an introduction to linux course and have to get a solution before the next lesson which is tomorrow. my problem is that one of the students didnt want to install linux in his laptops hard drive so he got an external usb hard drive in which we installed it, afterwards, when restarting the computer, when grub loads i get a grub error #21, it seems that the problem is that when i startup the computer, the usb external hard drive, which has the grub configuration files, isnt being mounted in startup, for now i have simply erased grub so the computer will automatically start windows up, but tomorrow the students will want to run linux from his hard drive, any suggestions are widely appreciated!! thanks in advance

p.s. grub error #21 simply says that it couldnt find its configuration files. also, beforer the grub error 21 i get a message saying it could find something (i cant remember what it says) and asks me to check the cable (im guessing it talks about the external usb hard drive)

---

### Post by wblancqu on 2008-03-14
Looks like your motherboard doesn't "see" your external HD in BIOS, and your HD is only seen AFTER loading your OS. The feature of recognizing external HD's at boot is only supported in newer motherboards.

What you can do to show your students linux:

- Just use a Live CD, and boot into the Live CD.
- Try WUBI (Installing Ubuntu as a Windows Progam)
- Try installing ubuntu in a virtual machine (and safe that Virtual Machine on the external HD). You can use VirtualBox or anything else for virtualization.
- Install Ubuntu @ home and remote access your Ubuntu Box by using VNC or NX or ... (make sure your router is setup correctly to forward the correct ports)

Good Luck

---

