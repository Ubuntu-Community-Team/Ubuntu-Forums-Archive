---
title: "How do I fix or remove Grub?"
date: 2009-08-20
forum: Installation &amp; Upgrades
---

### Post by monarda22 on 2009-08-20
I tried to install Hardy.  It didn't work and I have given up.  It crashed every 5 minutes.

I am now trying to get Xubuntu 9.04 up and running.

I made the SBM disk and got it to boot the CD and got Xubuntu installed on the hard drive I think but I can't boot to it.

Grub throws up with an error 2. 

I think if I could fix or remove Grub maybe I could get to the hard drive.

I Googled and I tried some stuff with dd and sda1 but it didn't work.  I tried some stuff with something caled Lilo but I really didn't understand what I was doing and couldn't make that work either.

Help?

Edit:  I guess I should add that this is a P III box (used to run Win NT) with 500+ RAM.  This is worth doing, right?

---

### Post by dstew on 2009-08-20
> This is worth doing, right?Yes, it is worth doing. Can you boot your Xubuntu install using Smart BootManager? Try that first.

If you can boot Xubuntu with SBM, then you know that the Xubuntu install is OK. If that is the case, look to see if the Xubuntu install has a /boot/grub/menu.lst file. That is grub's configuration file. If so, post it to the forum:```
cat /boot/grub/menu.lst
```Also post the output of```
sudo fdisk -l
```Then we can talk about re-installing grub.

If you want to try and re-install grub first, here is how to do it: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by monarda22 on 2009-08-20
Okay, I'll try that and report back.

---

