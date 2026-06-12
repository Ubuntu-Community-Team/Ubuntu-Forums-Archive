---
title: "Computer boots off of wrong sata interface"
date: 2008-12-04
forum: Hardware
---

### Post by Apocrathia on 2008-12-04
I have ubuntu running on an old asus a7n8x machine (athlon xp 2.0). The onboard sil3112a sata controller only had 2 ports, so I had to go get a new card. I ended up getting a sil3114 based pci card and hooking a front drive bay up to it. it worked fine, until I put drives into it. Apparently the computer gives the newer controller priority over the older one so the system looks for bootdata on the drives connected to the new card. however it exists on the old controller.
In my bios, there is no specific setting to change which sata controller, just an scsi boot option. I have been trying to update my bios (I have 1007 and newest is 1009) however it's next to impossible without a floppy drive. I have burned a couple of freedos livecd's and thrown the awdflash and bios.bin files on the iso but it doesn't seem to like that. I think I am going to grab an old floppy drive from work tonight and try updating with that but I have no idea if that would work either.
I have tried putting the boot drive on to the newer card and somehow that won't work either, I'm at a loss on that. One alternative I have though of is just to put grub or something on one of my new drives and boot from those and just point it to the boot data on the correct drive. I have no idea what else to do. I am going to try updating my bios first though.

---

### Post by razy60 on 2008-12-04
If you disconnect the new drives and reboot in the old drives could you not download and update the bios that way.

Raz

---

### Post by Apocrathia on 2008-12-04
I already have the new bios downloaded. 
when I disconnect the new drives everything runs perfectly. it's only when they're connected at boot time that it won't boot, which means I can't initialize my raid0 at boot time, which is a pain in the *** because mdadm doesn't want to work for me.
The update utility is a dos application. apparently the computer is just that old. I havent been able to find a non-dos update app for the asus a7n8x deluxe 2.0 motherboard. i can enter the utility at boot, however I need a floppy...

---

### Post by Apocrathia on 2008-12-04
updated the bios 1007 -> 1008 and an option of scsi <-> sata boot order was added. this fixed everything. hopefully this might help someone else.

---

