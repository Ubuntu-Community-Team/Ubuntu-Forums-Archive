---
title: "SD card is not even recognized"
date: 2009-07-22
forum: Hardware
---

### Post by powerplayground on 2009-07-22
Xubuntu 9.04 does not even recognize my SD card when XP, Vista and Arch Linux do so just fine. Only my hard drive shows up when i try fdisk -l or gparted. The card reader is actually my camera with the cable and it is via usb.

I heard on a few relating posts that there was a bug in ubuntu concerning some SD card readers, but the posts were unhelpful and just suggested I pay money to buy a new card reader. (Which may not even work.)

So is there a fix for SD cards in ubuntu / xubuntu or should I just nuke my laptop and start over with a more competent distro?

---

### Post by nixscripter on 2009-07-29
If Arch Linux worked, then it might just be a driver problem. Do you know what driver it used?

You can try **lspci -k** and **lsmod** to look at loaded drivers in Arch Linux.

---

