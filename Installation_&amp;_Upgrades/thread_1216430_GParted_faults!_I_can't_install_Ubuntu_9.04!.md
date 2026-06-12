---
title: "GParted faults! I can't install Ubuntu 9.04!"
date: 2009-07-18
forum: Installation &amp; Upgrades
---

### Post by fr0d0 on 2009-07-18
Good time.
I have a problem with installation linux on my hard disk. I can't install Ubuntu 9.04 and Linux Mint 7 on my hard disk because of GParted faults! Other utilities, for example, fdisk or cfdisk works without any problems. But GParted doesn't see any partitions on my hard disk. It says: "111Gb Unallocated space". And it is not the truth. Really I have 5 partitions:
20 Gb - NTFS system disk for windows
20 Gb - Ext3 system disk for linux
2 Gb - swap
48 Gb - NTFS
~20 gB - NTFS

And cfdisk application works with my disk perfectly. But GParted doesn't work (Unallocated space)
I don't know what to do. I tried to find faults on my hard disk but there is no problems with my computer and hardware.

How can I install Ubuntu or Mint? Maybe without GParted?
I'm waiting for your advices. Need help.

Best regards,
Theodore Biryukov.

---

### Post by presence1960 on 2009-07-18
Try the alternate text based installer. get it here: [alternate]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate")

---

### Post by lindsay7 on 2009-07-18
It could be a problem with the file allocation table. You could download TestDisk and run it and see if you get any errors to fix.  I do not think running Testdisk would harm anything.

---

### Post by fr0d0 on 2009-07-18
I'm very sorry. But I need an advice: how can I use TestDisk best, if I can't download it from linux?

---

### Post by lindsay7 on 2009-07-18
It is in Synaptic repos or you can search the web for their site and download it.

[ATTACH]121481[/ATTACH]

---

### Post by fr0d0 on 2009-07-18
Another question: maybe disk with gui-install also has alternate(text)-installation mode without gparted?

---

### Post by fr0d0 on 2009-07-20
mint@mint ~ $ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2d342d34

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2562    20579233+   7  HPFS/NTFS
/dev/sda2            2563       14593    96639007+   5  Extended
/dev/sda3            8574       11184    20972857+  83  Linux
/dev/sda5            2563        8311    46178811    7  HPFS/NTFS
/dev/sda6            8312        8573     2104483+  82  Linux swap / Solaris
/dev/sda7           11185       14593    27382761    7  HPFS/NTFS

Disk /dev/sdb: 8019 MB, 8019509248 bytes
175 heads, 32 sectors/track, 2796 cylinders
Units = cylinders of 5600 * 512 = 2867200 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2797     7831536    b  W95 FAT32

P.S.: Ubuntu and Mint are similar.

---

### Post by fr0d0 on 2009-07-20
I boot Mint from my usb flash disk (8 Gb). Why it displays 6 partitions on my /dev/sda ??

---

### Post by fr0d0 on 2009-07-20
I have tested my hard disk with Test Disk in Windows. There is no problems... ?

---

### Post by presence1960 on 2009-07-20
because fdisk is listing all disks. Those are the partitions on your internal HDD. sda is your internal 120 GB HDD and sdb is your flash drive.
fdisk -l reports all disks regardless of from which OS you are running the command.

---

### Post by fr0d0 on 2009-07-20
Yes. Really I have 5 partitions on /sda/ (my hard disk). What can you advice me to install ubuntu? How can I do it? :) Maybe I can try to delete needless partitions and run it? Beacause all partitions are free, except 2 (system and one home disk on ~40Gb).

Other: swap(2Gb), ext3(20Gb), ntfs(28Gb) - free

What can I try to do?:confused:

---

### Post by presence1960 on 2009-07-20
> **fr0d0 said:**
> Yes. Really I have 5 partitions on /sda/ (my hard disk). What can you advice me to install ubuntu? How can I do it? :) Maybe I can try to delete needless partitions and run it? Beacause all partitions are free, except 2 (system and one home disk on ~40Gb).

Other: swap(2Gb), ext3(20Gb), ntfs(28Gb) - free

What can I try to do?:confused:

```
mint@mint ~ $ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2d342d34

Device Boot Start End Blocks Id System
/dev/sda1 * 1 2562 20579233+ 7 HPFS/NTFS
/dev/sda2 2563 14593 96639007+ 5 Extended
/dev/sda3 8574 11184 20972857+ 83 Linux
/dev/sda5 2563 8311 46178811 7 HPFS/NTFS
/dev/sda6 8312 8573 2104483+ 82 Linux swap / Solaris
/dev/sda7 11185 14593 27382761 7 HPFS/NTFS
```

what is on sda3, sda5, sda6 & sda7? Please forget the windows jargon, it will only serve to confuse matters (such as system disk, etc) I posted your partition tabe for your sda disk. let me know what is on each partition so I can help you.

sda6 is swap. but what are the 2 NTFS partitions?

---

### Post by fr0d0 on 2009-07-20
About jargon - Ok! :D I'll try to. :D
sda1 - bootable, windows
One ntfs partition - 48Gb - simple data
Second ntfs partition - 28Gb - free space
If it's necessary I can delete this ntfs partitions, because all my data is on the other hard disk.
Linux & swap - ok
But what is extended partition?
Something else?

---

### Post by presence1960 on 2009-07-20
> **fr0d0 said:**
> About jargon - Ok! :D I'll try to. :D
sda1 - bootable, windows
One ntfs partition - 48Gb - simple data
Second ntfs partition - 28Gb - free space
If it's necessary I can delete this ntfs partitions, because all my data is on the other hard disk.
Linux & swap - ok
But what is extended partition?
Something else?
Each hard disk can have up to 4 partitions. The first type is primary- such as what windows is on. You can have one extended partition per hard disk. This is a special type that allows you to create as many logical partitions within that extended partition as your heart desires. The only limit is space available for that extended partition. So you can have a multitude of logical partitions inside an extended partition. But only one extended per hard disk.

You have a 120 GB disk, of which 48 GB is Windows. That leaves 72 GB to play with. Back up your data on that NTFS partition then using the Live CD or gparted Live CD delete all partitions except for Windows of course.  I would create 29 GB primary NTFS partition for data shared between Ubuntu and Windows. Then I would create a 43 GB extended partition. Within that partition I would create 12 GB for / (root) for Ubuntu- filesystem ext3 or ext4. Then I would make a 2 GB swap partition. The swap should be equal to your RAM if you want to use suspend & hibernate features. Whatever is left I would create an ext3 partition for Ubuntu storage. You can mark this as a separate /home partition during the install or just leave it as ext 3 for data. That is my partition scheme for your setup. of course there are many ways you can go. I just threw that out there for you as one example of what you can do.

I have a meeting at work I have to attend in a little bit, but will be back in a few hours.

---

### Post by allenbina on 2009-07-21
I'm having similar problems where grub works except I can't boot into ubuntu from the partitions its in.  I can boot into vista, and all the partitions show up in vista's disk manager, but even in the live disk, I can't see any partitions, the drive only shows up as "unallocated".

---

### Post by presence1960 on 2009-07-21
allenbina, in order to give and receive help more efficiently start your own thread and post the link back to it here. it can become quite confusing trying to help multiple people in the same thread.

---

### Post by allenbina on 2009-07-21
Sorry, my original thread is here [http://ubuntuforums.org/showthread.php?t=1216896](http://ubuntuforums.org/showthread.php?t=1216896) and somewhat related.  I will still follow this thread but not add any more to it.  sorry about that.

---

### Post by fr0d0 on 2009-07-22
I have installed Linux Mint - I solved my problem simply. I deleted all partitions except Windows and one NTFS. And gparted worked good after it. I don't know, what is the problem, but I solved it) Thanks.

---

### Post by fr0d0 on 2010-05-04
But it is the problem in gparted and it was really painfull for me. I've installed the latest version of Ubuntu (10.04, Lucid Lynx) and gparted in it has made all correctly (Now I have 5 partitions and gparted from other versions says that I can't have more than 4 primary partitions).

Does smb know what it means?

---

### Post by srs5694 on 2010-05-04
> **fr0d0 said:**
> But it is the problem in gparted and it was really painfull for me. I've installed the latest version of Ubuntu (10.04, Lucid Lynx) and gparted in it has made all correctly (Now I have 5 partitions and gparted from other versions says that I can't have more than 4 primary partitions).

Does smb know what it means?

I assume you mean "smb" to be an abbreviation for "somebody," rather than the acronym for Server Message Block (SMB), an early name for the protocol served by the Samba server.

The Master Boot Record (MBR) partitioning system used on most Linux systems is limited to four *primary* partitions, which are partitions defined in the first sector of the disk. One of these partitions may be of a special type (an *extended* partition) that can in turn hold an arbitrary number of *logical* partitions. If you've got four existing primary partitions, none of which is an extended partition, then you can't add more partitions to the disk, even if you resize your partitions so that you've got free space. There are several ways around this limitation, such as deleting one partition, converting at least one partition from primary to logical (a process with risks and limitations), and converting the entire disk from MBR to GUID Partition Table (GPT) form (a process with entirely different risks and limitations).

If you need more specific advice on this matter, you'll have to post your partition table. You can use a regular Linux installation or a Linux emergency disc and type the following command at a text-mode command prompt:

```

sudo fdisk -l

```

You can omit the "sudo" part on some emergency discs. You should also explain what you want to do -- for instance, shrink such-and-such a partition to make room for Linux.

---

