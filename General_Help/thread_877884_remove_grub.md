---
title: "remove grub"
date: 2008-08-02
forum: General Help
---

### Post by hirohitosan on 2008-08-02
Hi there. There is a way to remove grub from linux?

thanks

---

### Post by Titan8990 on 2008-08-02
Do you already have another bootloader such as LILO that you want to use?

---

### Post by hirohitosan on 2008-08-02
I failed install xubuntu and now I cannot start WinXP or Linux. I started linux from CD and I'm trying to restore Win

---

### Post by louieb on 2008-08-02
So you just want it to boot windows? 
Boot you windows CD and choose recovery mode.
Run the command fixmbr
Other ways here[IDBS Remove/Replace/Uninstal Grub]("http://www.users.bigpond.net.au/hermanzone/p18.htm")

---

### Post by hirohitosan on 2008-08-02
well my win has no CD recovery. My computer (IBM T40) has a hide partition on HDD from where I can recover win. So I have to restore MBR from linux.
any ideas ... please

---

### Post by hirohitosan on 2008-08-02
If i try fdisk it gives me this:

```
 sudo fdisk -l

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcccdcccd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1658    13313128+   c  W95 FAT32 (LBA)
Partition 1 does not end on cylinder boundary.
/dev/sda2            2385        4484    16866299    f  W95 Ext'd (LBA)
Partition 2 does not end on cylinder boundary.
/dev/sda3            1658        1746      710608+  82  Linux swap / Solaris
Partition 3 does not end on cylinder boundary.
/dev/sda4            1747        2384     5124735   83  Linux
/dev/sda5            3335        4484     9230728+   7  HPFS/NTFS
/dev/sda6            2385        3334     7630812   83  Linux
/dev/sda7            2385        2385           0+  83  Linux

Partition table entries are not in disk order

```

but if I start gparted it shows me that the disk is entirely unallocated.

any advices? 
thanks a lot

---

### Post by crazedgremlin on 2008-08-02
So you don't have an option to boot your Windows partition in GRUB?

---

### Post by hirohitosan on 2008-08-02
> **crazedgremlin said:**
> So you don't have an option to boot your Windows partition in GRUB?
NOPE, grub doesn't start: ERORR 22 and thats all :(

---

### Post by louieb on 2008-08-02
You can't restore the windows boot loader with the Ubuntu live CD.
Did you look at the link I gave. It has a list of other CDs that will do it.

BTW why did the install fail? Maybe you should just let the install finish and dual boot the computer.

---

### Post by crazedgremlin on 2008-08-02
This should fix GRUB:

(1)```
$ sudo grub
```

(2)```
grub> root (hd0,2)
```
[INDENT]*or whatever your partition is*[/INDENT]

(3)```
grub> setup (hd0)
```



source:
[http://www.jumpingbean.co.za/blogs/mark/grub_error_22](http://www.jumpingbean.co.za/blogs/mark/grub_error_22)


P.S. - Correct me if I'm wrong, but I believe that once you get GRUB working, you can boot into Windows and run the 'fixmbr' command

---

### Post by hirohitosan on 2008-08-03
ufff, it doesn't work
```
grub> root (hd0,2)

grub> setup (hd0)

Error 17: Cannot mount selected partition

```

---

### Post by louieb on 2008-08-03
> **hirohitosan said:**
> ufff, it doesn't work
```
grub> root (hd0,2)

grub> setup (hd0)

Error 17: Cannot mount selected partition

```
so close
candidates for you Ubuntu install are (hd0,3) and (hd0,5)
to find out which at the grub> prompt run
```
find /boot/grub/stage1
```
BTW: (hd0,2) is your swap partition.

use the output from the find command in your root statment. then run the setup (hd0) command.

BTW: (hd0,2) is your swap partition.

---

### Post by hirohitosan on 2008-08-03
well ... still not work

```
grub> root (hd0,3)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... no
 Checking if "/grub/stage1" exists... no

Error 15: File not found

```

and:

```
find /boot/grub/stage1
find: /boot/grub: No such file or directory

```

now I'm trying to get a WinXP CD to restore MBR

---

### Post by crazedgremlin on 2008-08-03
OK, good luck.  If that doesn't work out, here's a forum post that should help you out...
(check out post #2)
[http://www.linuxforums.org/forum/redhat-fedora-linux-help/66122-install-mbr-grub-knoppix.html](http://www.linuxforums.org/forum/redhat-fedora-linux-help/66122-install-mbr-grub-knoppix.html)

---

### Post by hirohitosan on 2008-08-04
hello 
I finally got an XP installer and I rewrite the MBR. Now I installed Linux again and I'm trying to save my data from the old NTFS partition.

How can I mount the NTFS partition?

Thanx

---

### Post by Titan8990 on 2008-08-04
You will use fdisk -l to find out the number for the partition. Lets say it is sda2 that is you NTFS partition. In order to mount it you would issue the following commands:

sudo mkdir /media/sda2

sudo mount /dev/sda2 /media/sda2


Your drive will then be mounted at the /media/sda2 location. I believe in Ubuntu it also usually puts mounted drives on your desktop.

---

