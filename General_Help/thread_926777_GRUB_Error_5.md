---
title: "GRUB Error 5"
date: 2008-09-22
forum: General Help
---

### Post by DarkPhoenixTSi on 2008-09-22
hey guys,

This has been giving me a headache. I am attempting to install Ubuntu 8.04 64bit on a server. It has a 60GB Hitatchi SATA drive, set as the primary HDD, and a 3ware SATA RAID controller, which I have partitioned into two 5TB drives.

The install goes flawlessly, on the 60GB Hitachi, yet when i go to boot the system, the GRUB (1.5) gives me a GRUB Error 5: Invalid or corrupted partition table. 

This would be the first time I am installing Ubuntu Server, but I attempted to install just the desktop version of 8.04, but I still get the same error.

Any help would be greatly appreciated.

PS: This is being set up as a file server (Samba installs with the OS) to store my movies on my home network.


Thanks again!!

Craig

---

### Post by werries on 2008-09-22
maybe you DO have a corrupted partition table. What does "sudo fdisk -l" look like if you mount in LiveCD? or maybe Gparted?

---

### Post by DarkPhoenixTSi on 2008-09-22
Actually, after I removed the SATA array from the equation, It seems to have cleared up the issue. What I had to do, was remove the drives from the array, reinstalled Ubuntu Server, and it booted. Then I plugged it all back up, and it started to boot. The only thing I can think of is that GRUB wants to boot off of the array first, and then from the other drive, regardless of what is set in the BIOS. 

I will post an update once all is done.

---

### Post by DarkPhoenixTSi on 2008-09-22
Figured it out. I had to unplug the drives before the install. After the install, I plugged them in, and they were recognised, without any errors. 

Now time to figure out a way to have ubuntu recognise them as a full 4.7TB drive.

---

### Post by fjgaude on 2008-09-22
One way would be to use **dmraid**... it is in the repository... the man pages tell all. 

Let us know how you are doing.

---

