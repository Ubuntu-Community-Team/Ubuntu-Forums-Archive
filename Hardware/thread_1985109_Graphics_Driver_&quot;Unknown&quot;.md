---
title: "Graphics Driver &quot;Unknown&quot;"
date: 2012-05-22
forum: Hardware
---

### Post by rjsec4ever on 2012-05-22
OS: 12.04 (Don't let stats fool you: cannot edit now til post 50.)
GFX: Nvidia GeForce GT520 1GB

Did a reinstall of the OS due to changing the partition table. Back to MBR now.
That being said, after reinstalling, I did not get anything Compiz related (jiggily windows, for one), due to having an 'unknown' driver.

[http://i.imgur.com/GGTrf.png](http://i.imgur.com/GGTrf.png)

---

### Post by sammiev on 2012-05-22
I get the same message as you and I have the Intel card. With another Linux OS it sees my Intel Ironlake card but still states I have a standard card which I have no issues with.

---

### Post by grahammechanical on 2012-05-22
Did you activate the Nvidia driver? Are you logged into Ubuntu 2D?

The Details utility does not detect the video card. Unknown driver and experience standard are what I have been getting since this Details utility was first introduced when I use using 12.04 as it was being developed.

I am now using 12.10 development release and I still see the same message even though I am using the Nouveau open source driver. I think that this is a long standing issue.

If you are in Ubuntu and not Ubuntu 2D, if you have Compiz Configuration Settings Manager installed, then you should be able to set wobbly windows at least. I have it working even with Nouveau. This will be especially true if you are using the Nvidia drvier.

Regards.

---

### Post by Axxon95 on 2012-05-23
I have found after doing "sudo apt-get install mesa-utils", "Unknown" has been replaced with the Hardware's name(if supported).
I found this out by my Father's NVIDIA GPU computer(with Ubuntu-X Team NVIDIA drivers), and my Sister's Intel GMA GPU netbook.

I don't know if this will help, but just a little info to replace Unknown with the correct name.

---

### Post by rjsec4ever on 2012-05-23
> **Axxon95 said:**
> I have found after doing "sudo apt-get install mesa-utils", "Unknown" has been replaced with the Hardware's name(if supported).
I found this out by my Father's NVIDIA GPU computer(with Ubuntu-X Team NVIDIA drivers), and my Sister's Intel GMA GPU netbook.

I don't know if this will help, but just a little info to replace Unknown with the correct name.

+1. That has helped alleviate the "unknown" field, but the experience is still set to Standard. When I had 11.10 on here and upgraded, I get the middle option... whatever it was.

> **grahammechanical said:**
> Did you activate the Nvidia driver? Are you logged into Ubuntu 2D?

I am using the post-release nVidia drivers, and no, I an in the regular 'Ubuntu'.

> **grahammechanical said:**
> If you are in Ubuntu and not Ubuntu 2D, if you have Compiz Configuration Settings Manager installed, then you should be able to set wobbly windows at least. I have it working even with Nouveau. This will be especially true if you are using the Nvidia drvier.

That *might* be the issue I've been having all along! I didn't install CCSM!

EDIT: It WAS! Now, to get the perfect eye candy configuration... without the desktop cube and whatnot.

................

*Another reformat. Working on a tri-boot with Win7 on one drive and kubuntu with the Ubuntu install on another. I don't want any hassle with a GNOME/KDE conflict in Ubuntu, especially in terms of KDE removal. Booting towards primary drive (Win7). Using EasyBCD to direct the WinBootMgr to the Linuxes, but I had used only one extended partition... now 3 primaries and 1 extended (2 logicals). NOT converting to GCT, as it has issues with Windows (MBR-only). I am also talking about GRUB issues . Another story to follow... ;)*

---

