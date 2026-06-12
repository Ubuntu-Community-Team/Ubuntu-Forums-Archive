---
title: "Upgrade computer (PATA --&gt; SATA)"
date: 2006-04-08
forum: Hardware &amp; Laptops
---

### Post by g00fy on 2006-04-08
Hi,


Can someone tell me how I can move my current Ubuntu installation from a PATA disk to a SATA disk?


Thanks!
Steven

---

### Post by amohanty on 2006-04-08
Re-install ??

What exactly do you want to move? The entire OS, some folders? Do you intend to discard the PATA?

AM

---

### Post by g00fy on 2006-04-08
Sorry to be so cryptic ;-)

I want to move the entire OS.
I want to discard the PATA drive after the process is finished (or put windows xp on it to play some games ;)).

Thx

---

### Post by jpkotta on 2006-04-08
It should be no different from going PATA -> PATA.  You should install the new disk in your computer, and boot.  

Partition your new disk, which should be automatically detected as /dev/sda or similar, with cfdisk, fdisk, gparted, or whatever you want.  

For the least pain, reboot with a live CD. In the live CD environment, mount all of the partitions, both old and new.  Assume that you have a /home, /, and swap partitions, and you have picked the same partition layout for your new disk, and on both disks / is on part 1, swap is on part 2, and /home is on part 3
```
mkdir /new/home /new/root /old/home /old/root
mount /dev/hda1 /old/root
mount /dev/hda3 /old/home
mount /dev/sda1 /new/root
mount /dev/sda3 /new/home
cp -a /old/root /new/root
cp -a /old/home /new/home

```

Next you will have to edit /new/root/etc/fstab.  You would just have to edit it to mount sda partitions instead of hda.  

Then redo the bootloader.  Edit /new/boot/grub/menu.lst and change the line that looks like
```
# groot=(hd0,0)
```
to something like
```
# groot=(hd1,0)
```
and run update-grub.  There is more information about grub in the wiki.  The thing to know is that grub labels hard disks differently than Linux.  

Finally, 
```
umount /old/home /old/root /new/home /new/root
```

And reboot.  Hopefully it will work and I didn't forget anything.  Don't worry if this all sounds complicated.  In any case, you will not kill your current PATA install, maybe just mess up the MBR, which is easily fixed.

---

### Post by amohanty on 2006-04-10
jpkotta's solution is bang on target. Let us know how it goes.

AM

---

### Post by g00fy on 2006-04-10
Hi all ;),

I'm back on Ubuntu... But it didn't went as smooth as that... I just partitioned, copied everything and stuff... But still wouldn't start. No system disk and stuff (everything ok from bootflag to bios, so I don't know what went wrong).

Then I reinstalled simply, and copied all the necessary data over to my new installation.

Had some problems (again) with my wireless (it's a pita to install :().

Works ok now :D.


Thanks for your help, but I don't know what went wrong :S

---

### Post by amohanty on 2006-04-11
Kind of late to figure out what went wrong :) 
Good to know that you got things working again.

AM

---

