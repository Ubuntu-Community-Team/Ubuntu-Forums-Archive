---
title: "help me to make dual-boot ubuntu and xp"
date: 2009-05-24
forum: Installation &amp; Upgrades
---

### Post by mgph on 2009-05-24
Hi, I'm having a problem to install Window XP (Ubuntu 9.04 installed first).

I create unallocated space with gparted using Ubuntu Live CD. Then, when I booted up with XP cd, the installer said 
"Setup did not find any hard disk drives installed in your computer"

Why ? I've tried to change the unallocated space partition format to NTFS but still the same. I've already read run-through at these two links to figure out what's happening but because of my stupidity, I still don't understand and don't know how to solve it to be able to install XP.

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=3](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=3)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

Can someone help me ? please.

Thanks in advance

---

### Post by lisati on 2009-05-24
It's usually easier to install XP first, partly because XP likes to think it's the "first" OS on the system, and partly because the Ubuntu installer is friendlier to any other OS you might have on your system.

---

### Post by logos34 on 2009-05-24
> **mgph said:**
> Hi, I'm having a problem to install Window XP (Ubuntu 9.04 installed first).

I create unallocated space with gparted using Ubuntu Live CD. Then, when I booted up with XP cd, the installer said 
"Setup did not find any hard disk drives installed in your computer"


possibilities:

1. the unallocated space is inside an extended partition (windows needs a primary partition because of the bootloader)

2. The space is on another disk, which is in slave or second position (windows will refuse to install unless the target drive is the boot drive/in first position)

---

### Post by mgph on 2009-05-24
For XP install first advice, sorry dude. I have to do image for all the data first, delete and reformat the whole hdd, and then install XP. Also risky, also time consuming. I know installing Ubuntu is the most user-friendly(noobs like me) OS I've ever seen, but for this case, I simply can't do :( anyway, thanks

For hard drive partition problem, I have only one drive and no partition at all (only for swap place). So, for my case, this is not possible. I think so because of gparted as well.

guys, please help me make dual-boot with Ubuntu and XP on XPS 1530.

thanks

---

### Post by logos34 on 2009-05-24
hmmm...maybe gparted messed up the partition table so windows can't read it...

post output of

sudo fdisk -l

you could try to fix it with [testdisk]("http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#Save_the_partition_table_or_search_for_more_partitions.3F")

---

### Post by mgph on 2009-05-24
Thanks logos, for trying to help me. This is the output of your suggested command "sudo fdisk -l".

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000080

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19925   160047531   83  Linux
/dev/sda2           37596       38913    10586835    5  Extended
/dev/sda5           37596       38913    10586803+  82  Linux swap / Solaris

I think what you've guessed, it seems like missing the partition I make for windows. I haven't formatted that partition yet and because of that ? 

Appreciate your help.....

---

### Post by logos34 on 2009-05-24
looks ok...the unallocated space is bewteen sda1 and sda2, cyls. 19926-37595

But there's something else that's causing windows installer to be confused, because you should be able to put windows right there in second position

You might checkthe Bios hard disk settings--if this is a sata disk maybe ubuntu is using 'AHCI' mode, in which case either change the mode back to ide or install sata drivers from floppy beforehand (F6 option)

---

### Post by presence1960 on 2009-05-24
try creating a partition from the unallocated space and formatting it as NTFS. You can do this with gparted. Then the Windows installer will recognize the partition. Windows installer does not recognize Linux partitions as being able to be installed to so it thinks you have none.

Sorry I didnt see you already tried that. my bad!

---

