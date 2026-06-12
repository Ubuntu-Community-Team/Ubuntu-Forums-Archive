---
title: "Grub trouble"
date: 2007-02-17
forum: Hardware &amp; Laptops
---

### Post by phido on 2007-02-17
**SOLVED**
I need help, I've added a new-old harddisk to my system and now I have trouble with grub which sits in the mbr, I've booted right now with the "[super grub disk]("http://adrian15.raulete.net/grub/")". I've read around and tried alot but I always get an ["Error 22" (partition not found)]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#Grub_Errors").

fdisk -l output
```
Disk /dev/hdc: 120.0 GB, 120059854848 bytes
255 heads, 63 sectors/track, 14596 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1       14596   117242338+  83  Linux

Disk /dev/sda: 120.0 GB, 120060444672 bytes
255 heads, 63 sectors/track, 14596 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        5737    46082421    7  HPFS/NTFS
/dev/sda2   *        5738       14596    71159917+  83  Linux

Disk /dev/sdb: 120.0 GB, 120060444672 bytes
255 heads, 63 sectors/track, 14596 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb3               1       14596   117242338+   5  Extended
/dev/sdb5               1         149     1196748   82  Linux swap / Solaris
/dev/sdb6             150        4628    35977536   83  Linux
/dev/sdb7            4629       14596    80067928+   b  W95 FAT32

```and my menu.lst (the important part), I know root needs to be (hd2,5) but how, I wasn't able to change it permanently :confused:
```

title        Ubuntu, kernel 2.6.17-11-generic
root        (hd1,5)
kernel        /boot/vmlinuz-2.6.17-11-generic root=/dev/sdb6 ro vga=794
initrd        /boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot

title        Ubuntu, kernel 2.6.17-11-generic (single-user mode)
root        (hd1,5)
kernel        /boot/vmlinuz-2.6.17-11-generic root=/dev/sdb6 ro single
initrd        /boot/initrd.img-2.6.17-11-generic
boot

title        Ubuntu, memtest86+
root        (hd1,5)
kernel        /boot/memtest86+.bin
quiet
boot
```

---

### Post by bernied on 2007-02-17
Are you able to boot to your ubuntu install using the super grub disk?

If yes, then do the grub setup from there, because when you are running the super grub disk, grub may see that as one of your disks, and sneakily change the order, so that when you try to setup the mbr, you are trying to write to the cd.

---

### Post by bernied on 2007-02-17
When you boot (without the super grub disk) do you get the grub menu? Or does it not get that far?

---

### Post by phido on 2007-02-17
Yes, I could boot with the SGD, but I couldn't change/restore the mbr, don't know if it was me or the system ;)
And I couldn't get into the grub menu, the error happen while loading it.

---

### Post by bernied on 2007-02-17
OK, so you can try this if you are willing.

1 - using the SGD, boot up ubuntu and log in (maybe you are already there)
[EDIT]1a - remove the cd from the drive[/EDIT]
2 - open a terminal
3 - get a grub console by typing
```
sudo grub
```and supplying your password when asked
You should now be in a grub console which looks a bit weird
4 - type
```
root (hd1,5)
```
Do not continue if you get an error at this point - post the error here
5 - type (without hitting <enter> at the end)
```
cat /
```
then hit the <TAB> key. At this point you should get a list of the files and directories in your root 
directory. (This should be the same as output from 'ls /' in a terminal.)
Does this list look right? If yes, then you have the right partition. 
If not, do not continue - go to step 7
6 - type (but only if you are sure you've got the right partition) 
```
setup (hd0)
```That should be you fixed. Yes?

7 - Only do this if that list was all wrong. Try that 'root (hdx,y)' command with different combinations of x and y, followed by the 'cat /' and using tab-completion, until you find the right partition, then do step 6.

Does this work?

---

### Post by phido on 2007-02-17
I've fixed it, I followed [this]("http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD") instructions found in another thread, and wrote the mbr in every disk I have (setup (hd0-2)) and after a reboot I could boot into grub.
To start ubuntu I had to change the boot command from (hd1,5) to (hd2,5) and I could launch it.
So after the first boot I've edited my menu.lst and now everything (seems) to work fine - I can launch ubuntu and windows.
Probably dirty - but it works and I can sleep well. :D

Thx for your help

---

### Post by bernied on 2007-02-17
Excellent!

---

