---
title: "I can't install ubuntu hardy heron cause  (initramfs)"
date: 2008-12-07
forum: Installation &amp; Upgrades
---

### Post by Spetimuz on 2008-12-07
Hy all,
I was an Edgy eft user but I have serious probs to update packages. Then I've tried to install a newer version ( Hardy Heron) in the way i know: 
download iso image, burn a dvd, run as install dvd and so on...
now i can't do it more because after i've chosen the install ubuntu option, an unknown prompt appairs (initramfs). 
What happened?!? The provided online help cannot help me at all.
[-o<
The installation process stops. I'm looking for news across the forums but without any success yet. The question is easy I think. How to install the OS. I know ther is wubi.exe but i prefer to format my hd tby using the unix standards with gparted. The prob is that my present hd has already two partitions and i can't add another one eg. in d partition. If the only system is wubi, i'll prefer another distro. Since  i like Ubuntu a lot and i think my prob depends simply on a basic quirk, please give me an help and workaround.
Thanks in advance
Speti

---

### Post by Spetimuz on 2008-12-11
> **Spetimuz said:**
> Hy all,
I was an Edgy eft user but I have serious probs to update packages. Then I've tried to install a newer version ( Hardy Heron) in the way i know: 
download iso image, burn a dvd, run as install dvd and so on...
now i can't do it more because after i've chosen the install ubuntu option, an unknown prompt appairs (initramfs). 
What happened?!? The provided online help cannot help me at all.
[-o<
The installation process stops. I'm looking for news across the forums but without any success yet. The question is easy I think. How to install the OS. I know ther is wubi.exe but i prefer to format my hd tby using the unix standards with gparted. The prob is that my present hd has already two partitions and i can't add another one eg. in d partition. If the only system is wubi, i'll prefer another distro. Since  i like Ubuntu a lot and i think my prob depends simply on a basic quirk, please give me an help and workaround.
Thanks in advance
Speti

As I've read in an online guide, I've tried to work so:
wait 60 seconds and type exit
In theory the installation should go on but my system simply reboots. Now I've installed succesfully Feisty Fawn, but I have too update problems. I need to update to 8.04 or 8.10 But I can't. Please help.

---

### Post by Spetimuz on 2008-12-12
> **Spetimuz said:**
> As I've read in an online guide, I've tried to work so:
wait 60 seconds and type exit
In theory the installation should go on but my system simply reboots. Now I've installed succesfully Feisty Fawn, but I have too update problems. I need to update to 8.04 or 8.10 But I can't. Please help.

I think I've solved the installation problem burning the ubuntu-8.04.1-desktop-i386.iso on a cd. The OS now works but I have neverending problems to update packages. Is it possible to find the proper repos? This is the report of Hardy Heron as I try to install nvidia drivers and others:
The connection starts terribly slow with dsl and it is no possible to display web content in Firefox. And there are difficulties in update packages. messages says: Impossibile ottenere [http://it.archive.ubuntu.com/ubuntu/dists/hardy/main/i18n/Translation-it.bz2](http://it.archive.ubuntu.com/ubuntu/dists/hardy/main/i18n/Translation-it.bz2)  
Impossibile ottenere [http://it.archive.ubuntu.com/ubuntu/dists/hardy/restricted/i18n/Translation-it.bz2](http://it.archive.ubuntu.com/ubuntu/dists/hardy/restricted/i18n/Translation-it.bz2)  
Impossibile ottenere [http://it.archive.ubuntu.com/ubuntu/dists/hardy/universe/i18n/Translation-it.bz2](http://it.archive.ubuntu.com/ubuntu/dists/hardy/universe/i18n/Translation-it.bz2)  
Impossibile ottenere [http://it.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/i18n/Translation-it.bz2](http://it.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/i18n/Translation-it.bz2)  ...W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.24/nvidia-glx-new_169.12+2.6.24.13-19.42_i386.deb](http://archive.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.24/nvidia-glx-new_169.12+2.6.24.13-19.42_i386.deb)  404 Not Found [IP: 91.189.88.45 80] Failed to contact server.

---

