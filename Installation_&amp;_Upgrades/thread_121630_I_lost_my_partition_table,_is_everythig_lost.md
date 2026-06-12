---
title: "I lost my partition table, is everythig lost?"
date: 2006-01-25
forum: Installation &amp; Upgrades
---

### Post by Zalbor on 2006-01-25
Out of stupidity, I copied the MBR from my second hard drive (the MBR to loadGRUB) to my first hard drive (which has/had all ubuntu and windows partitions)!!!
Now, of course, the partition table is lost too. I'm using LIVE. Is there any way to restore the partition table, or have I lost everything? I really hope I won't have to reinstall everything!

---

### Post by RavenOfOdin on 2006-01-25
You copied the MBR?

I don't think all of your data would be lost unless you installed another operating system on top of your pre-existing one/formatted the partition.

Try using BootIt NG ([http://terabyteunlimited.com](http://terabyteunlimited.com)) to fix your MBR.

---

### Post by Zalbor on 2006-01-25
I think the partitions must still be there, since all I changed was the MBR, but no OS can see them now. Will BootIt help with that? I'll try it, I guess.

---

### Post by hillbilly on 2006-01-25
Iam not sure, but I thnk the boot loader would have some option to recreate the mbr. Iam not sure how, but logically it should. Iam at work so cannot go after this immediately. But try reading the documentation on the boot loader you use.

---

### Post by Zalbor on 2006-01-25
Well, they told me that there must be some program that scans the whole hard drive, recognizes the partitions and rebuilds the table. Does anyone know of one?

---

### Post by az on 2006-01-25
If you borked your MBR, your partitiontable is fine.  You just need to reinstall grub back onto your MBR.  If your linux install is on, say, hda5, chroot into it and install grub

sudo mount /dev/hda5 /mnt
sudo chroot /mnt
sudo grub-install /dev/hda
reboot.


If your partition table is borked, you can use parted to rescue lost partitions.

You run parted from the command line.
sudo parted /dev/hda
print
(that will show the partition table)  

Read the manual to use the rescue option.  It should not be too difficult.  You enter "rescue" and then input the beginning of where you think your lost partitionis.  Do it for all of your partitions.  Good luck.

---

### Post by mjunior on 2006-01-25
Hi,

Can you boot up from a live Ubuntu CD?
If you could do so, I think the lilo can fix the MBR config by the #lilo command on the shell.
Can you boot by Windows CD?
If you could so or if at least you could get access to DOS, you can find the linux kernel location from there and then use the same tip above.
On the cmd you'll need to reasearch for two files on linux partition or cd:Loadlin and vmlinuz
If you find those files copy them into your C:\linux temporarily. Then type:
C:\linux\loadlin.exe C:\linux\vmlinuz root=/dev/hda1[1] ro 
[1] shift hda1 for hda2,hda3 or whatever partition is in ( you can do it by scratch if you can't recall).

After recovering the mbr access, log into your linux normaly and then fix the line related to windows by editing /etc/lilo.conf

Hope it helps.

---

### Post by Zalbor on 2006-01-25
I'm beginning to fear something more than the partition table is wrong... Parted, fdisk and all those can't see any partitions at all, nor can the shell... See here, for example:
```
ubuntu@ubuntu:~$ ls /dev/sd*
/dev/sda  /dev/sda1

```
```

ubuntu@ubuntu:~$ sudo fdisk -l /dev/sda
Warning: ignoring extra data in partition table 5
Warning: ignoring extra data in partition table 5
Warning: ignoring extra data in partition table 5
Warning: invalid flag 0x0c46 of partition table 5 will be corrected by w(rite)

Disk /dev/sda: 120.0 GB, 120000000000 bytes
255 heads, 63 sectors/track, 14589 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               2        1245     9992430    f  W95 Ext'd (LBA)
/dev/sda5   ?        1374      143409  1140892742+  39  Plan 9

```
```

ubuntu@ubuntu:~$ sudo parted /dev/sda
GNU Parted 1.6.21 with HFS shrink patch 16
Copyright (C) 1998 - 2004 Free Software Foundation, Inc.
This program is free software, covered by the GNU General Public License.

This program is distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY; without even the implied warranty
of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the GNU General Public License for more details.

Using /dev/sda
(parted) print
Error: Invalid partition table on /dev/sda - wrong signature c46
Ignore/Cancel? i
Disk geometry for /dev/sda: 0.000-114440.917 megabytes
Disk label type: msdos
Minor    Start       End     Type      Filesystem  Flags
1          7.844   9766.076  extended              lba
(parted)

```

See what I mean? There should be sda1 and sda5, 6 and 7... Is it something I'm doing wrong or has all data been deleted? Can't see how that would be though, all I did was rewrite the first 512 bytes on /dev/sda with dd...

---

### Post by Zalbor on 2006-01-26
Anyone, please? I don't understand how to use parted rescue...

---

### Post by lha on 2006-01-26
[QUOTE=Zalbor]Well, they told me that there must be some program that scans the whole hard drive, recognizes the partitions and rebuilds the table. Does anyone know of one?[/QUOTE]

Look at [gpart]("http://www.stud.uni-hannover.de/user/76201/gpart/"). It scans your hd and tries to guess where partitions used to be.

---

### Post by markcaetano@gmail.com on 2006-01-26
there is a minimalistic linux that fits on a floppy that repairs ext2 &ext3 partitions and out of dumb luck the win partition might shift its wayward ass and get working

the disto i mentioned is called HAL 91 and can be found [HERE]("http://www.hal91.com")

---

### Post by Zalbor on 2006-01-26
[QUOTE=lha]Look at [gpart]("http://www.stud.uni-hannover.de/user/76201/gpart/"). It scans your hd and tries to guess where partitions used to be.[/QUOTE]
Yes, yes, yes! Thank you a great lot! That was perfect! It found all the partitions and rewrote the table, then all I had to do was reinstall GRUB (the safe way this time ;)) and it's all back to normal.

---

