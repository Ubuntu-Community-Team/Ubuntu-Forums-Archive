---
title: "Iomega Zip 100 -- A Blast from the Past"
date: 2007-01-22
forum: Hardware &amp; Laptops
---

### Post by skewray on 2007-01-22
I am trying to get an Iomega Zip 100 to work on 6.10.  The paralle port is set to bi-directional, and the ppa module is loaded, while the lp module is not (no printer).  No scsi devices show up at all in /proc.  Any suggestions?

Brian

---

### Post by edemark on 2007-01-22
When i used iomega paralel-port i had to load imm modeule but it was in slackware. You might try modprobe it.
them mount it. If i am not mistaken generally it showes up as sda4

hope it helps

---

### Post by skewray on 2007-01-23
From my reading around the forum, the Iomega 100 requires ppa and Iomega 250 requires imm.  Always one for experimentation, I tried imm, but it did not work either.  With ppa I got a new directory /proc/scsi/ppa.  With imm, nothing happens, as far as I can tell.  In either case, no new scsi devices.

---

### Post by edemark on 2007-01-23
Hi
So i am of course not certain as i have not used my zipdisk for a while but if i recall corectly to use it i was doing the following
1., load module
sudo modprobe imm
2., create directory in mnt for the zip
sudo mkdir /mnt/iozip
3., mounting zip
sudo mount -t auto /dev/sda4 /mnt/iozip
4., browse to /mnt/sda4 with nautilus

the tricky part is the 3rd step as if you have for ex sata hd (that i do not as i have ide) than the device not might not be sda4. Can be sdb4 or sdb0 or many other things.
What i suggest is that you observe carefully /dev directory befour and after the first step to see if you find wich is the new device.(ls /dev command can be usefull)
Of course you can try the other module not imm but imm did work for me with my 100MB parport iomega zip drive

good luck

---

### Post by skewray on 2007-01-23
Even after loading the module, there is no /dev/sda4 to mount.  That is the problem.  There is no /dev/sda<anything>.

---

### Post by edemark on 2007-01-23
can you send the result of the following command 
ls /dev
make it twice before and after mounting the module 
Actually which module yue are using? IMM? 

pd it can be sdb sdc etc. depending how is your system

---

### Post by edemark on 2007-01-23
one more thing 

you have to power on your box with the zip connected as parport devices get scanned only during the boot process. So if you are trying to connect your zip to a powered system it will not get reconized. In the same way you should disconnect parport devices when system is off.

just in case

---

