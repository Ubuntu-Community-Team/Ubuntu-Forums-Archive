---
title: "HELP!  Cant unmount partition, need to unmount to install"
date: 2009-07-22
forum: Installation &amp; Upgrades
---

### Post by Theory5 on 2009-07-22
I have a problem. I used a small 2 gb partition to put my ubuntu installation there so I could install ubuntu. Unfortunatly the damn installer needs to unmount that partition in order to make a few changes. help?

---

### Post by merlinus on 2009-07-22
Use gparted on the live cd, or gparted live.

---

### Post by Theory5 on 2009-07-22
I dont have a livecd. It somehow uses the flash drive to boot off the partitioned space. and it wont boot from anything except that and the flash drive must be in the computer as well.

---

### Post by merlinus on 2009-07-22
gparted live is a small download:

[http://sourceforge.net/projects/gparted/files/](http://sourceforge.net/projects/gparted/files/)

Download the .iso and burn as a disk image, not a data disk, at no more than 4x.  Then boot from it.

You cannot do anything with mounted partitions, and in your situation need a live cd.

---

### Post by Theory5 on 2009-07-22
I can use unetbootin to install it on a flash drive right?

---

### Post by merlinus on 2009-07-22
Worth a try...

---

### Post by raymondh on 2009-07-22
The flash drive may have live session capability (hence gparted as well) ... assuming OP installed Ubuntu from the flash drive.

@ theory5, are you re-partitioning because of the boot problem? Or are you accessing gparted to extned/enlarge Ubuntu?  Or both?

---

### Post by Theory5 on 2009-07-22
yes, and even after using gparted it wont work. For some reason, when I make a live usb flash drive, it doesnt work unless I have that usb drive as well as the same stuff on a hdd partition that can only be on my internal harddrive.
idk what i did but now its letting me continue on. I then selected Install them side by side in the Prepare disk space menu and its at 0% for resizing the partition. I will post again if this does not work.

nope now it says it cannot make the changes. So yea I need some help.
Great I made it through most of the installation, but now its having trouble transfering files for some reason, it keeps crashing the installtion.

---

### Post by raymondh on 2009-07-22
> **Theory5 said:**
> yes, and even after using gparted it wont work. For some reason, when I make a live usb flash drive, it doesnt work unless I have that usb drive as well as the same stuff on a hdd partition that can only be on my internal harddrive.
idk what i did but now its letting me continue on. I then selected Install them side by side in the Prepare disk space menu and its at 0% for resizing the partition. I will post again if this does not work.

nope now it says it cannot make the changes. So yea I need some help.
Great I made it through most of the installation, but now its having trouble transfering files for some reason, it keeps crashing the installtion.

Help us understand.  What did not work?  Resizing or installation? 

I read/responded to your other thread involving the bootloader. Because of that, I am assuming you have Ubuntu already installed in the internal HD and this thread is about resizing that partition.

---

### Post by Theory5 on 2009-07-23
I have no trouble resizing it with Gparted. BUT Ubuntu 9.04 during installation, needs to make changes to the partitions and to do that it wants to unmount any part of my harddrive that is mounted, but it cant because the only way ubuntu will boot on my laptop is by putting it on the internal harddrive in a partition. Thus the problem, sorry that I wasnt clear enough.

---

### Post by raymondh on 2009-07-23
> **Theory5 said:**
> I have no trouble resizing it with Gparted. BUT Ubuntu 9.04 during installation, needs to make changes to the partitions and to do that it wants to unmount any part of my harddrive that is mounted, but it cant because the only way ubuntu will boot on my laptop is by putting it on the internal harddrive in a partition. Thus the problem, sorry that I wasnt clear enough.

No worries.

Access a terminal (applications > accessories), type (or copy and paste) and post pack the output:

```
sudo fdisk -l
``` (small L not 1 nor i)

Also, if can you post a screenshot of what gparted is showing you, it'll help the forum visualize.  Sda would be your internal and the flash/thumb drive would be sdb or sdc.  

Do I/we disregard your other thread and assume that UBUNTU **was** never installed in the internal HD? 

What program did you use to make a liveUSB?

Note:  When using gparted from a live session (or a live gparted), better to also have SWAP in SWAPOFF mode.

---

