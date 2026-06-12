---
title: "UBUNTU + XP + Vista problem"
date: 2009-05-22
forum: Installation &amp; Upgrades
---

### Post by alucito on 2009-05-22
Hi, i have a hp laptop, it came with vista and a recovery partition, i hated vista, so i created a new partition and i installed xp.
I just installed Ubuntu 9.04 i deleted the vista partition, and i created a new one for ubuntu. my problem is, that when i get the grum window, i only can pick between ubuntu and vista recovery partition, but i cannot see the xp anywere.

I remember that when i installed Xp, i had to run a program so xp could be booted, so i managed the booting system through vista, but right now i dont have vista installed cuz i deleted the partition, so i guess ubuntu's booting program does not recognize xp (im just guessing probably im completly wrong). is there a way to get into grum's options and configure that so it could recognize xp.

Thanks Very much.
As u can see im new at this, so please try to be clear

---

### Post by presence1960 on 2009-05-22
run these commands in terminal and post the output of each back here
> sudo fdisk -l BTW that is a lowercase L 

> gksu gedit /boot/grub/menu.lst That is a lowercase L in .lst

P.S. Open a terminal by going Applications > Accessories > Terminal

---

### Post by alucito on 2009-07-17
here is my fdisk -l results 


Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5c195c19

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               2       28554   229351972+   f  W95 Ext'd (LBA)
/dev/sda2   *       29088       30401    10554705    7  HPFS/NTFS
/dev/sda5               2       12749   102398278+   7  HPFS/NTFS
/dev/sda6           12750       28554   126953631   83  Linux


and this is my menu.lst result (only important stuff)



title        Ubuntu 9.04, kernel 2.6.28-13-generic
uuid        afeae87c-0ce7-4032-a4c5-99722d688b32
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=afeae87c-0ce7-4032-a4c5-99722d688b32 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-13-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid        afeae87c-0ce7-4032-a4c5-99722d688b32
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=afeae87c-0ce7-4032-a4c5-99722d688b32 ro  single
initrd        /boot/initrd.img-2.6.28-13-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic OLD
uuid        afeae87c-0ce7-4032-a4c5-99722d688b32
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=afeae87c-0ce7-4032-a4c5-99722d688b32 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode) OLD
uuid        afeae87c-0ce7-4032-a4c5-99722d688b32
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=afeae87c-0ce7-4032-a4c5-99722d688b32 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        afeae87c-0ce7-4032-a4c5-99722d688b32
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title Microsoft Windows Xp
root (hd0,4)
savedefault
makeactive
chainloader +1

title        Windows Vista (loader)
rootnoverify    (hd0,1)
savedefault
makeactive
chainloader    +1



I know is kinda late for replies but just in case.
it took me so long cuz I had a problem, I tried to install again Xp, but a problem with the table came, I wasn't able to boot any OS, so I erased evererything again, and install xp, and ubuntu all over.(i still have the vista recovery) 
but i still have the same problem, the results are from the new ones.
Thanks for the help

---

### Post by konnorrigby on 2009-07-17
boot from the live cd go to g-parted.

it is in administration i belive. i may be wrong.

now erase everything and  install Windows XP first then Ubuntu.

if this does not work you prolly need a new cd or cd's.

hope i helped.

---

### Post by oldfred on 2009-07-17
Check that your UUID's are correct.  The command is :

blkid

This will give you your UUID's by partition. Verify that your menu.lst has the correct uuid.
Your fdisk -l showed sda6 as you linux root and sda2 as your windows boot.
 if sda2 is corect the boot stanza labeled Vista should boot you into XP. I have versions that use both root & rootnoverify, but without the makeactive line. Try 
root     (hd0,1) on the XP line and # (comment out the makeactive line on the Vista line. If one works then edit again to correct name and/or delete incorrect line.

---

### Post by lisati on 2009-07-17
Looking at the fdisk output, I suspect that one of your Windows partitions has been reused, possibly your main Vista partition. My laptop, after a fresh destructive install of Vista from a recovery DVD, followed by installation of 64-bit Ubuntu 9.04 shows two NTFS partitions, one of which is the recovery partition. If XP was there as well, I'd expect a third NTFS partition.

---

### Post by gilanib on 2009-07-17
Salam,
 
My name is Mubashir Gilani. I am new in Ubuntu 9.04 OS.
I read the documentation and read that Ubuntu use ext3 file system. If I install Ubuntu in my PC in C drive "which is NTFS formated drive". Did my other partitions are hide or remove when I install Ubuntu??
 
Please help.
 
Best Regards!!
 
 
Thanks!!

---

### Post by presence1960 on 2009-07-17
> **gilanib said:**
> Salam,
 
My name is Mubashir Gilani. I am new in Ubuntu 9.04 OS.
I read the documentation and read that Ubuntu use ext3 file system. If I install Ubuntu in my PC in C drive "which is NTFS formated drive". Did my other partitions are hide or remove when I install Ubuntu??
 
Please help.
 
Best Regards!!
 
 
Thanks!!

Please don't ask for help in someone else's thread. it makes it difficult for  everyone involved to give and receive quality help. please start your own thread!

---

### Post by alucito on 2009-07-18
here is the blkid results


/dev/loop0: TYPE="squashfs" 
/dev/sda2: UUID="2C88743C8874071C" LABEL="HP_RECOVERY" TYPE="ntfs" 
/dev/sda5: UUID="84307DF6307DF012" TYPE="ntfs" 
/dev/sda6: UUID="afeae87c-0ce7-4032-a4c5-99722d688b32" TYPE="ext3" 

my guess is that sda2 is vista recovery, sda5 is Xp, and sda6 es Ubuntu.
but now, my problem is that i cannot get to boot Xp.

if im not mistaking, the menu.lst should be like the one i have, hd(0,1) for vista loader and hd(0,4) for Xp right?
but i still don't get whats doing wrong, if i do it like that, error 12 comes up when im trying to boot Xp.

---

### Post by merlinus on 2009-07-18
xp is on (hd0,4), linux on (hd0,5).  But my guess is your problem ls caused by xp installed on a logical rather than primary partition.

Also notice where the parentheses go...

---

### Post by alucito on 2009-07-18
Hi, Thanks Everybody for the replies, the problem was solved
The problem was that i thought that the sda5 was Xp, but i was wrong, aparently that's the Vista Recovery partition, the sda1 is the Xp partition, so the Xp booter was the one that title was vista loader.
Im gonna change that, is really easy, but still i cannot get access to de vista recovery partition.
any ideas?

---

