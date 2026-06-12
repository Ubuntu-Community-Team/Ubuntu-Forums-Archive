---
title: "Dual-Boot Problems"
date: 2009-09-14
forum: Installation &amp; Upgrades
---

### Post by xiainx on 2009-09-14
Hello all,
I'm trying to dual boot my Dell XPS M1730 with Windows Vista, and Ubuntu, but having some trouble...
First let me state that I have spent hours searching these forums and google for the answer, and have been unable to find a suitable solution, so I'm posting here. The problem is...
I can shrink my windows partition just fine, and now I have 10 GB of unallocated space (I tried formatting FAT32, but the same problem occurred). Now, I can go ahead and boot from the Ubuntu CD, but when I try to install, gparted says that I have no other operating systems installed. But I do! Why does it say this, and how can I get it to detect my windows installation? I am not tampering with the windows installation, and I understand that Ubuntu should be able to work just fine as a dual boot, however I'm having troubles with it.
Any help would be appreciated.

---

### Post by v1nsai on 2009-09-14
That's odd that it doesn't detect your Windows install.

All the detection process is doing is adding entries to /boot/grub/menu.lst which is used by GRUB to choose which OS to boot.The cool thing about Linux is that if automated stuff fails, you can just do it yourself :guitar:

Go ahead and install Ubuntu, don't worry about the windows detection thing, as long as you install to the right partition on your HDD windows will still be there.  Once your in Ubuntu we need to figure out what drive letter your windows partition was assigned.  Open a terminal by clicking on Applications > Accesories > Terminal and type in 
```
sudo fdisk -lu
```
to find it.  The windows partition will look something like this
```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3824    30714880    7  HPFS/NTFS
```

Next, type this in the terminal
```
sudo gedit /boot/grub/menu.lst
```
to open up the GRUB boot list.  Scroll down to the bottom and copy/paste this to the bottom
```
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```

The 'root' line is the only line you will have to change there if your system is different from mine.  Luckily, GRUB and fdisk use two different formats for naming devices, so /dev/sda1 is the same as (hd0,0) on my system.  If you only have one HDD and Windows is installed to the first partition, you can just use the code I posted it will be the same on your system.  Otherwise, you have to count.  Use the result from the fdisk command I had you run earlier and use the '/dev/sdxx' part to figure out what to put in root.  /dev/sda1 = hd0,0; /dev/sda2 = hd0,1; /dev/sda3 = hd0,2 and so on.

If you get confused, post the results of 
```
sudo fdisk -lu
```
and I'll help you set up the menu.lst entry.  Linux gives us problems, but it gives us the power to solve them without overly complex means.

---

### Post by xiainx on 2009-09-14
All of that sounds like a good plan, but gparted doesn't detect my hard drive partitions! In order to install ubuntu, I will need to either repartition my hard drive, or install it to the entire hard drive, neither of which I want to do, as these will overwrite my windows install! Basically, I stated the problem wrong, it's not detecting my *partitions*, so I can't install it without risk...

---

### Post by v1nsai on 2009-09-14
Are you sure?  I've definitely never heard of that problem before.  When it starts up the partitioner and it asks you if you want to use one of the 'Guided' options, is there a 'Manual' option to select?  That's the one that shows you all of your partitions and lets you do it yourself.

---

### Post by xiainx on 2009-09-14
I will try it again, and take some screenshots, maybe I'm being a dummy, but I can't figure it out for the life of me!

---

### Post by xiainx on 2009-09-14
It gives me the option to specify my partitions manually, however, after advancing to this, it turns out that this is just reformatting my hard drive and partitioning with gparted. It does not detect that I have already partitioned it!

---

