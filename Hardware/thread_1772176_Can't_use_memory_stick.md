---
title: "Can't use memory stick"
date: 2011-05-31
forum: Hardware
---

### Post by Marnie on 2011-05-31
Hi.  :)  Hoping someone has an answer to the below problem.  Newbie here - so step by step instructions needed.

I'm having a problem adding files onto my USB memory stick.  When I try I get the following message: 

"Error opening file '/media/usb0/New Document.ott': Permission denied"

This is my computer, so I'm the admin on the computer.  There is only one other profile on the computer and she is listed as a desktop user only.  Is there a way to change the permissions so that I can use this device? 

These are my computer details
Toshiba Satellite X200
Ubuntu 11.04 
Gnome 2.32.1
Kernel 2.6.38-9-generic
GCC version 4.5.2 (x86_64-linux-gnu)
The memory stick I am using is a Lexar

---

### Post by sanderj on 2011-05-31
Can you *view* the contents of the stick? 

If so, it's probably a rights problem. See the two command below how to check: mount and sudo fdisk. See details below.


```
sander@R540:~$ mount | grep media
/dev/sdb1 on /media/2C40-D68D type vfat (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)
sander@R540:~$ 


sander@R540:~$ sudo fdisk -l /dev/sdb
Disk /dev/sdb: 1039 MB, 1039663104 bytes
65 heads, 32 sectors/track, 976 cylinders
Units = cylinders of 2080 * 512 = 1064960 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         977     1015280    6  FAT16
Partition 1 has different physical/logical endings:
     phys=(991, 64, 32) logical=(976, 15, 32)
sander@R540:~$ 


```

---

### Post by Marnie on 2011-05-31
Yes, I can see the contents, just can't copy too.

This is what I get after inputing the above commands . . .

root@ubuntu:/home/marnie# 65 heads, 32 sectors/track, 976 cylinders
root@ubuntu:/home/marnie# Units = cylinders of 2080 * 512 = 1064960 bytes
root@ubuntu:/home/marnie# Sector size (logical/physical): 512 bytes / 512 bytes
bash: syntax error near unexpected token `('
root@ubuntu:/home/marnie# I/O size (minimum/optimal): 512 bytes / 512 bytes
bash: syntax error near unexpected token `('
root@ubuntu:/home/marnie# Disk identifier: 0xc3072e18
root@ubuntu:/home/marnie# sudo fdisk -l /dev/sdb
root@ubuntu:/home/marnie# $ sudo fdisk -l /dev/sdb
root@ubuntu:/home/marnie# Disk /dev/sdb: 1039 MB, 1039663104 bytes
root@ubuntu:/home/marnie# I/O size (minimum/optimal): 512 bytes / 512 bytes
e# I/O size (minimum/optimal): 512 bytes / 512
nie# I/O size (minimum/optimal): 512 bytes
e# I/O size (minimum/optimal): 512 bytes / 512

---

### Post by sanderj on 2011-05-31
Have you posted the output of 'mount | grep media'?

---

### Post by Marnie on 2011-05-31
nope, because I have no idea how to do that.  :-k

TOTAL Newbbie here.  I'm a dog person, not a computer person.  :lolflag: @ me.

---

### Post by dFlyer on 2011-05-31
At command line type:

mount | grep media

make sure your usb device is plugged in and press enter.

Hightlight entry on screen and post.

---

### Post by coffeecat on 2011-06-06
Sorry, I've only just come across this thread. This:

> **Marnie said:**
> "Error opening file '[COLOR=Red]/media/usb0[/COLOR]/New Document.ott': Permission denied"

The '/media/usb0' is the giveaway. Uninstall the application usbmount and the usb automounting functionality built into Ubuntu will work as it should. The app usbmount should not be used on GUI desktop systems.

---

