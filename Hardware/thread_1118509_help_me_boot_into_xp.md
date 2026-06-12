---
title: "help me boot into xp"
date: 2009-04-07
forum: Hardware
---

### Post by imdeemvp on 2009-04-07
hello forum,

partitioning is my weakest knowledge when it comes to linux...

i have the following issue:

1) ubuntu installed in primaray sata hd
2) xp installed in secondary sata hd

here is my fdisk:> imdeemvp@power2liv:~$ sudo fdisk -l
[sudo] password for imdeemvp: 

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00081901

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       37435   300696606   83  Linux
/dev/sda2           37436       38913    11872035    5  Extended
/dev/sda5           37436       38913    11872003+  82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x084af365

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               2       45894   368635522+   f  W95 Ext'd (LBA)[B]
/dev/sdb2   *       45895       60801   119740477+   7  HPFS/NTFS[/B]
/dev/sdb5               2       45894   368635491    7  HPFS/NTFS


now can someone here help me enter the line for the grub!! I tried different hd setting but i must be doing something wrong so here is my grub config:
> 
title Ubuntu 8.04.2, kernel 2.6.24-23-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-23-generic root=UUID=a1889941-9672-4a64-b42d-6b16b7ec88da ro quiet splash
initrd /boot/initrd.img-2.6.24-23-generic
quiet

title Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode)
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-23-generic root=UUID=a1889941-9672-4a64-b42d-6b16b7ec88da ro single
initrd /boot/initrd.img-2.6.24-23-generic

title Ubuntu 8.04.2, memtest86+
root (hd0,0)
kernel /boot/memtest86+.bin
quiet

title Other operating systems:
root 

title 		WINDOWS XP Proffesional	
root		(hd2,0)
savedefault
makeactive
map		(hd0)	(hd2)
map		(hd2)	(hd0)
chainloader +1

thanks in advance!!:popcorn:

---

### Post by Anthon on 2009-04-07
Why are you referring to hd2 in your menu.lst file? There seem to be only two drives, would those not be hd0 (the linux one) and hd1 (the XP one).

---

### Post by mhgsys on 2009-04-07
I Agree with Anthon, 
meaning 

```
title WINDOWS XP Proffesional
root (hd2,0)
savedefault
makeactive
map (hd0) (hd2)
map (hd2) (hd0)
chainloader +1 

```

should be changed to 
```

title WINDOWS XP Professional
map (hd0) (hd1)
map (hd1) (hd0)
rootnoverify (hd1,0)
chainloader +1 


```

---

### Post by meierfra. on 2009-04-07
> Device Boot Start End Blocks Id System
/dev/sdb1 2 45894 368635522+ f W95 Ext'd (LBA)
/dev/sdb2 * 45895 60801 119740477+ 7 HPFS/NTFS
/dev/sdb5 2 45894 368635491 7 HPFS/NTFS 

Your partition table has some serious problems. The primary partition /dev/sdb2 sits inside the extended partition /dev/sdb1 and also inside the logical partition /dev/sdb5.

To figure out  how to fix the partition table, I suggest to boot into  Ubuntu and  download the Boot Info Script to  your desktop:

[https://sourceforge.net/projects/bootinfoscript/]("https://sourceforge.net/projects/bootinfoscript/")

Then open a terminal (Applications > Accessories > Terminal) and type:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post (use the code tags)

In addition I suggest to analyze the partition table with testdisk:

Download the [testdisk-6.10.linux26.tar.bz2 package](http://www.cgsecurity.org/testdisk-6.10.linux26.tar.bz2) to your desktop, and then do:

```


cd ~/Desktop
tar xvf testdisk-6.10.linux26.tar.bz2
sudo testdisk-6.10/linux/testdisk_static  /dev/sdb

```

After starting testdisk with the above command, choose
"Proceed",
"Intel",
"Analyze",
"Quick search",
Press "Y" (to search for Vista partitions)
Press "Enter" to continue,
select "Deeper Search" (so it does a deeper search, which could take a while)

Please post the output of the screen that has the deep search results. Also, use your up/down arrow keys to select each partition listed in the deep search results, and press "p" to get a directory listing; please let me know exactly which partitions give you a directory listing.

---

