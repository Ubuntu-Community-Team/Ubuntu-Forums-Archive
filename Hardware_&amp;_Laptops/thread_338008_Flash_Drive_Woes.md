---
title: "Flash Drive Woes"
date: 2007-01-13
forum: Hardware &amp; Laptops
---

### Post by Pobega on 2007-01-13
I'm trying to mount a flash drive I got for free from Citibank, but it doesn't want to work! First I did:

> root@ackbar:~# ls /dev | grep sd
ptysd
sda
sda1
sda2
sda3
sda5
sdb
ttysd

Then:

> root@ackbar:~# mkdir /mnt/citibank/
root@ackbar:~# mount -t auto /dev/sdb /mnt/citibank/
mount: No medium found

Any help would be appreciated.

---

### Post by puneit on 2007-01-13
Run ```
lsusb
``` at terminal 
This will display the connected USB devices. If your Flash drive doesn't list there, then probably the drive is faulty. To be sure, check it on another machine, if you can. Maybe through a Live CD, or another OS. But better another machine altogether

---

### Post by Pobega on 2007-01-13
> pobega@ackbar:~$ lsusb
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 1976:6025  
Bus 002 Device 001: ID 0000:0000

The only thing I have plugged in is the Flash card, so I guess this means it isn't faulty?

---

### Post by Pobega on 2007-01-14
Bump up to the top, I paid such good money for this and I'd like to get it work </sarcasm>

---

### Post by azemute on 2007-01-14
you were close, instead of listing the contents of /dev, look at the kernel log. insert the device and run:

> dmesg | tail

after that, you'll get some output mostly regarding the last device connected. the majority of which will be sd*. Assuming that it used sda, you can try mounting that partition exactly the same way as you did in your third command.

> mount /dev/sda /mnt/citibank -t auto

normally usb keys come partitioned out of the box with a single primary partition, so you shouldn't have any problems there. If it's not partitioned, or there's more than one partition [like if you were trying to mount your windows partition or somesuch] then you can use 

> fdisk -l /dev/sda

to list all the partitions on that drive. [of course, I'm assuming all through here that it detected it at sda, if it found sdb, substitute that]

good luck.

---

### Post by AusIV4 on 2007-01-14
Is the flash drive formatted? When I plug in my flash drive and run 

ls -l /dev/sd*

I get /dev/sda AND /dev/sda1.

/dev/sda1 is the one that should be mounted. I assume your flash drive is /dev/sdb, and it looks to me like it isn't formatted. Open up gparted or qtparted (get them from repositories if necessary), and your flash drive should be listed as an available device. Format it as FAT32 or ext3, then it should mount automatically when you plug it in.

---

### Post by Pobega on 2007-01-15
> **azemute said:**
> you were close, instead of listing the contents of /dev, look at the kernel log. insert the device and run:



after that, you'll get some output mostly regarding the last device connected. the majority of which will be sd*. Assuming that it used sda, you can try mounting that partition exactly the same way as you did in your third command.



normally usb keys come partitioned out of the box with a single primary partition, so you shouldn't have any problems there. If it's not partitioned, or there's more than one partition [like if you were trying to mount your windows partition or somesuch] then you can use 



to list all the partitions on that drive. [of course, I'm assuming all through here that it detected it at sda, if it found sdb, substitute that]
 
good luck.

It ended up working out to be sdb1, thanks so much! :D

---

### Post by Pobega on 2007-01-15
I think something got messed up, how do I remove everything from the drive in a safe fashion?

> pobega@ackbar:/media$ sudo rm -r usbdisk/*
Password:
rm: cannot remove `usbdisk/\002\001.\004\001': Read-only file system
rm: cannot remove `usbdisk/\n\001.\f\001': Read-only file system
rm: cannot remove `usbdisk/\022\001.\024\001': Read-only file system
rm: cannot remove `usbdisk/ad error. -': Read-only file system
rm: cannot remove `usbdisk/ldlinux.sys': Read-only file system
rm: cannot remove `usbdisk/\r\nsyslin.UX/&#9508;&#9552;&#9566;\033zl&#9564;K.4ê\025/ë&#8805;5r~&#9577;\177&#9553;.·Éÿ/.&U&#9564;&#9575;2vp.&#9573;&#402;\023': Read-only file system
rm: cannot lstat `usbdisk/\r\nsyslin.UX/&#9508;&#9552;&#9566;\033zl&#9564;K.4ê\025/ë&#8805;5r~&#9577;\177&#9553;.·Éÿ/&#9484;&#9552;&#9570;{&#8729;Ö\020Å.)&#9580;»': Input/output error

---

### Post by Pobega on 2007-01-15
Nevermind, I got it working by removing the old partition in GParted, sorry!

---

