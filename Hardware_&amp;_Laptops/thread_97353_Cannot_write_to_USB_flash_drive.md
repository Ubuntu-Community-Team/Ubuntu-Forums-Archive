---
title: "Cannot write to USB flash drive"
date: 2005-11-30
forum: Hardware &amp; Laptops
---

### Post by VirtualMe on 2005-11-30
Hi everyone.  First time using Ubuntu, and Linux for that matter.
I'm trying to copy some directories from my WinXP box to my flash drive through Ubuntu.  Only problem is it won't work!

If I try to create a new folder on the drive, it says it is a read-only file system.  And if I try to paste a file into a folder already on the drive it says I don't have permission.  I just installed Ubuntu yesterday, and haven't done anything to the system to mess it up in anyway.

My question is, what do I need to do to be able to write files to my flash drive?  It's not encrypted or write protected in any way.

Thanks for any and all help.

---

### Post by aysiu on 2005-11-30
Make sure your USB drive is plugged into your computer.
Then, go to Applications > Accessories > Terminal.
Type these three commands in ```
sudo fdisk -l
df -h
cat /etc/fstab
``` Then, highlight your entire terminal and copy and paste all of the text into a new post in this thread.

---

### Post by VirtualMe on 2005-11-30
Okay aysiu, here we go.


virtualme@Imperator:~$ sudo fdisk -l

Disk /dev/hda: 60.0 GB, 60011642880 bytes
16 heads, 63 sectors/track, 116280 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       81930    41292688+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/hda2           81935      112934    15623212+  83  Linux
Partition 2 does not end on cylinder boundary.
/dev/hda3          112934      116280     1686825    5  Extended
Partition 3 does not end on cylinder boundary.
/dev/hda5          112934      116280     1686793+  82  Linux swap / Solaris

Disk /dev/sda: 262 MB, 262144000 bytes
32 heads, 33 sectors/track, 484 cylinders
Units = cylinders of 1056 * 512 = 540672 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         485      255984    b  W95 FAT32
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(0, 1, 1) logical=(0, 0, 33)
Partition 1 has different physical/logical endings:
     phys=(254, 31, 33) logical=(484, 27, 5)

virtualme@Imperator:~$ df -h

Filesystem            Size  Used Avail Use% Mounted on
/dev/hda2              15G  1.8G   13G  13% /
tmpfs                 380M     0  380M   0% /dev/shm
tmpfs                 380M   13M  367M   4% /lib/modules/2.6.12-10-386/volatile
/dev/hda1              40G  2.3G   38G   6% /media/hda1
/dev/sda1             249M   34M  216M  14% /media/CRUZER MINI

virtualme@Imperator:~$ cat /etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     ntfs    defaults        0       0
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by aysiu on 2005-11-30
A couple of these lines concern me:
[QUOTE=VirtualMe]
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         485      255984    b  W95 FAT32
[b]Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(0, 1, 1) logical=(0, 0, 33)
Partition 1 has different physical/logical endings:
     phys=(254, 31, 33) logical=(484, 27, 5)[/b][/quote] Is your USB flash drive partitioned? How is it partitioned?

> [b]
/dev/hda1       /media/hda1     ntfs    defaults        0       0[/b] Are you able to read off of your Windows XP drive (it should be read-only)? *defaults* usually means only root can read it.

---

### Post by Mattias on 2005-12-01
Hello I've got similar problems with an ASONO flash mp3 player.It automounts perfectly but when I try to write to it it claims to be a read only filesystem.
df -l gives 
> Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/hda5             14684136   8201180   5886304  59% /
tmpfs                   517980         0    517980   0% /dev/shm
tmpfs                   517980     12644    505336   3% /lib/modules/2.6.12-10-686/volatile
/dev/hda7             18147912  10880236   6714640  62% /home
/dev/hdb1            122907761  51441093  68750560  43% /media/hdb1
/dev/hda1             37664360  23322980  14341380  62% /media/ckolon
/dev/hda8             44968016  23294400  21673616  52% /media/partition2
/dev/sda1            115377640  23439424  86077304  22% /media/usbdisk
/dev/sdb                507408         8    507400   1% /media/usbdisk-1

and fdisk -l gives
> Disk /dev/sdb: 520 MB, 520617984 bytes
17 heads, 59 sectors/track, 1013 cylinders
Units = cylinders of 1003 * 512 = 513536 bytes

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   ?      775809     1913904   570754815+  72  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(357, 116, 40) logical=(775808, 8, 13)
Partition 1 has different physical/logical endings:
     phys=(357, 32, 45) logical=(1913903, 14, 4)
Partition 1 does not end on cylinder boundary.
/dev/sdb2   ?      168185     2098423   968014120   65  Novell Netware 386
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(288, 115, 43) logical=(168184, 16, 27)
Partition 2 has different physical/logical endings:
     phys=(367, 114, 50) logical=(2098422, 8, 24)
Partition 2 does not end on cylinder boundary.
/dev/sdb3   ?     1864289     3794527   968014096   79  Unknown
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(366, 32, 33) logical=(1864288, 10, 12)
Partition 3 has different physical/logical endings:
     phys=(357, 32, 43) logical=(3794526, 1, 20)
Partition 3 does not end on cylinder boundary.
/dev/sdb4   ?     2877051     2877106       27749+   d  Unknown
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(372, 97, 50) logical=(2877050, 0, 3)
Partition 4 has different physical/logical endings:
     phys=(0, 10, 0) logical=(2877105, 5, 41)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order


---

### Post by VirtualMe on 2005-12-01
[QUOTE=aysiu]A couple of these lines concern me:
 Is your USB flash drive partitioned? How is it partitioned?

 Are you able to read off of your Windows XP drive (it should be read-only)? *defaults* usually means only root can read it.[/QUOTE]

My flash drive shouldn't be partitioned.  It is the same as when I bought it.  What command can I run to view the partitions on it?

As for reading off my XP drive, I tried reading hda1 through the file browser and it say's I don't have permission.  Although, the XP I want to read from is over the network on my desktop machine.  I'm using Ubuntu on my laptop.  I can read from my desktop machine just fine, which is to be expected.

For future reference, how would I be able to read from hda1?  I don't see anyway to  do so through the file browser.

---

### Post by Ghuloomo on 2008-02-27
This problem have a long history. I have tried every solution to get my friend's 4 GB usb flash to work, but no use.

See this thread too:
[http://ubuntuforums.org/showthread.php?t=237881&page=3](http://ubuntuforums.org/showthread.php?t=237881&page=3)

---

