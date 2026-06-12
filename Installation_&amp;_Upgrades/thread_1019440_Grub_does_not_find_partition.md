---
title: "Grub does not find partition?"
date: 2008-12-23
forum: Installation &amp; Upgrades
---

### Post by creznedmick on 2008-12-23
Greetings
My trouble seems to be grub in my new installation of 8.1 not properly identifying its partition and thus not writing to the MBR.
I have two hard drives, one ATA the other SATA. Although the SATA drive; which contains the three active partitions (Vista, Ubuntu 8.1, Ubuntu8.4) is the first to load in the bios,they are sdb1, sdb5, sdb6. The ATA drive is identified as hda.  

 Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        3825    30724281    7  HPFS/NTFS
/dev/sdb2            3826        9244    43528117+   f  W95 Ext'd (LBA)
/dev/sdb4           29704       30401     5606685    7  HPFS/NTFS
/dev/sdb5            3826        5610    14337981   83  Linux
/dev/sdb6            5611        7395    14337981   83  Linux
/dev/sdb7            7396        9180    14337981   83  Linux
/dev/sdb8            9181        9244      514048+  82  Linux swap / Solaris

I use two Linux partitions for Ubuntu so I can install the latest and move files,emails, favourites, settngs etc as I like. All worked and works well in the 8.4 (sdb6) boot menu. After installing 8.1 when I rebooted it reloaded the 8.4 Grub menu.
I mounted and did a chroot into 8.1 (on sdb5). I ran grub and tried

grub> find /boot/grub/stage1

Error 15: File not found    -It is there

grub> root(sd1,4)

Error 27: Unrecognized command

grub> root(hd0,4)

Error 27: Unrecognized command


The entry recognised in 8.4 for the partition (previously occupied by 7.1) was 

# linux installation on /dev/sdb5.
title		Ubuntu 7.10, kernel 2.6.22-14-generic (on /dev/sdb5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=72f0b024-c2ed-41ce-bc08-78d3d5d360f6 ro quiet splash 
initrd		/boot/initrd.img-2.6.22-14-generic
savedefault
boot

 The entry for 8.1 is

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		92f4ae4a-32cd-45d0-ae1e-6bc3eaf052e0
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=92f4ae4a-32cd-45d0-ae1e-6bc3eaf052e0 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

I am Stuck. Any help greatly appreciated
Michael

---

### Post by Herman on 2008-12-23
:) Hello creznedmick,
You should be able install Intrepid Ibex's GRUB to MBR without chrooting, providing the required GRUB files are present in the partition, in the /boot directory.

From a live CD, try,
```
sudo grub
``````
find /boot/grub/stage1
``````
root (hd0,4)

```NOTE: There's a space between the word 'root', and the '(hd0,4)'
Feel free to replace '(hd0,4) with (hd1,4) if the earlier command indicates that number for your hard disk.
```
setup (hd0)
``````
quit
```

---

### Post by Herman on 2008-12-23
You should be able to do that from 8.04 if you prefer, you don't really need a Live CD when you already have another Ubuntu installed.

---

### Post by creznedmick on 2008-12-23
Greetings
Thanks Herman. You were right, a simple typo
Michael

---

