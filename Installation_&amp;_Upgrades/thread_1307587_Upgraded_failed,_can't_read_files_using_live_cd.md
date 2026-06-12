---
title: "Upgraded failed, can't read files using live cd"
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by toddfryar on 2009-10-31
My attempted upgrade to 9.10 failed.  I have tried fixing it using many suggestions with no luck.  Now I just want to backup my data and install fresh but I am getting permission errors when trying to copy data.

Can someone please point me to a useful article on how to backup my data to an external HD with the live CD?

Thanks!

---

### Post by viralmeme on 2009-10-31
> **toddfryar said:**
> My attempted upgrade to 9.10 failed.  I have tried fixing it using many suggestions with no luck.  Now I just want to backup my data and install fresh but I am getting permission errors when trying to copy data.

Can someone please point me to a useful article on how to backup my data to an external HD with the live CD?

Thanks!

What kind of external hd, usb or what ?. If you get permission errors then you need to login as root or sudo to access those files.

01. plugin the external hd and boot from the CD.

02. From the menu, run Applications->Accessories->Terminal

03. At the command prompt type (without the $ sign) 

$ sudo bash
$ df -kTh

The bootable CD auto mounts any harddrives at /mnt. So ( assuming hda1 is your hd and sda1 is your external hd) you type

$ cp /mnt/hda1/home/* /mnt/sda1/ -pr 
--

If you can't see the external hd then you need to mount it. If it's a usb then it's named /dev/sda1 or sda2 etc. You can mount it to your system and copy over your files eg:

$ mkdir /mnt/usbdrive
      
 $ mount /dev/sda1 /mnt/usbdrive

$ cp /mnt/hda1/home/* mnt/sda1/ -pr

---

### Post by deadpool47 on 2009-11-08
Okay, I'm having the same issue and I can't get this insane thing to do what I want with the Live CD, either. I tried all that code and it didn't work. I'm in the root directory, but the punk won't detect my drives. Here's what I got after getting a requisition of info from the root:

> Filesystem    Type    Size  Used Avail Use% Mounted on
aufs          aufs    1.6G   48M  1.6G   3% /
udev         tmpfs    1.6G  268K  1.6G   1% /dev
/dev/sr0   iso9660    691M  691M     0 100% /cdrom
/dev/loop0
          squashfs    666M  666M     0 100% /rofs
none         tmpfs    1.6G  200K  1.6G   1% /dev/shm
tmpfs        tmpfs    1.6G   12K  1.6G   1% /tmp
none         tmpfs    1.6G   88K  1.6G   1% /var/run
none         tmpfs    1.6G     0  1.6G   0% /var/lock
none         tmpfs    1.6G     0  1.6G   0% /lib/init/rw
/dev/sdb1     vfat    932G  129G  803G  14% /media/1DF7-382A
/dev/sda1     ext3    679G  348G  297G  54% /media/e4c127a2-c947-44ae-b011-6823578374a4


From my guess the sdb1 is my main drive where the data is stuck in, and the sda1 is my external. For the love of all things holy, someone help! I got a file I worked very hard on on the desktop and I would hate to lose it!

---

### Post by presence1960 on 2009-11-08
[http://www.remote-exploit.org/backtrack.html](http://www.remote-exploit.org/backtrack.html)

Download backtrack Linux and make a bootable CD. This has never failed me yet, especially on clients' machines which were unbootable.

---

