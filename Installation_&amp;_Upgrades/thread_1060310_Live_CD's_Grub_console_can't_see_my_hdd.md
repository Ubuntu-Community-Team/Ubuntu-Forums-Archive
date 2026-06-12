---
title: "Live CD's Grub console can't see my hdd"
date: 2009-02-04
forum: Installation &amp; Upgrades
---

### Post by supernova123 on 2009-02-04
I am using an eee pc 900 and so I have two hard drives, /dev/sda (4gb) and /dev/sdb (16gb), as shown below:
[quote="sudo fdisk -l"]
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 4034 MB, 4034838528 bytes
255 heads, 63 sectors/track, 490 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8eb98eb9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         489     3927861    7  HPFS/NTFS

Disk /dev/sdb: 16.1 GB, 16139354112 bytes
255 heads, 63 sectors/track, 1962 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000a4a12

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1          51      409626   83  Linux
/dev/sdb2              52        1962    15350107+   5  Extended
/dev/sdb5            1875        1962      706828+  82  Linux swap / Solaris
/dev/sdb6              52        1791    13976487   83  Linux
/dev/sdb7            1792        1874      666666   82  Linux swap / Solaris

Partition table entries are not in disk order
[/quote]

Now, Ubuntu 8.10 was installed on /dev/sdb (sdb6), and I installed another distro on /dev/sda1 (no swap file). The new distro removed the mbr from the /sdb (I think) and installed lilo on /dev/sda1.

Now, whichever hard drive I set as the first in the boot order, Lilo always appears. 

I wanted grub back, so I downloaded the latest live CD (lost mine) and tried to install grub on /dev/sda1.

[quote=grub]
 [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub> find /boot/grub

Error 15: File not found

grub> device (hd0) /media/sda1

Error 15: File not found

grub> device (hd0) /dev/sda

Error 15: File not found

grub> device (hd0) /dev/sda1

Error 15: File not found

grub>
[/quote]

But the live cd grub doesn't see my hard drives! The fdisk -l above was taken from the live cd as well - so ubuntu sees them!

My plan is to install grub on /dev/sda1 and be able to boot to both distros by setting the menu.lst file. Is this the right thing to do?

It's just really annoying that I can't get grub to see something that Ubuntu does! I don't understand!

Any help would be greatly appreciated.

Edit: I tried making sure the drives were mounted:
*ubuntu@ubuntu:~$ sudo mkdir /media/sdb1 && sudo mkdir /media/sdb6 && sudo mount /dev/sdb1 /media/sdb1 && sudo mount /dev/sdb6 /media/sdb6 && sudo mkdir /media/sda1 && sudo mount /dev/sda1 /media/sda1*
But still no luck :(

---

### Post by logos34 on 2009-02-04
they don't need to be mounted to do what you did (counterintuitive though it may seem).

You say you installed another 'distro', yet sda1 filesytstem type shows (windows) NTFS (???)

> The new distro removed the mbr from the /sdb (I think) and installed lilo on /dev/sda1.

Did you try booting without sda connected?

---

### Post by caljohnsmith on 2009-02-04
Did you remember to run grub with "sudo grub" and not just "grub"? If you just use "grub", you can get those "file not found" errors when the files actually exist. 
[QUOTE=supernova123]```
grub> find /boot/grub
```[/QUOTE]
When you use the "find" command with Grub, you have to give it a file, not a directory, so you should do something like:
```

sudo grub
grub> find /boot/grub/[COLOR="Blue"]stage1[/COLOR]
```
How about trying that and posting the results.

---

