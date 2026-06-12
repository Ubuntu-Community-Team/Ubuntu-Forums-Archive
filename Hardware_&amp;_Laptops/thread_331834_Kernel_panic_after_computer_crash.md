---
title: "Kernel panic after computer crash"
date: 2007-01-05
forum: Hardware &amp; Laptops
---

### Post by SirIdefix on 2007-01-05
My notebook sometimes gets very hot so it shutdowns automaticly. After one of these crashes ubuntu wouldn't boot anymore. It says: "Kernel panic - Not syncing VFS: unable to mount root FS on unknown block" . Before the crash I had an ubuntu update (with the update manager).
How can I get ubuntu to boot again (Sorry, I am an absolute newbie)?

---

### Post by SirIdefix on 2007-01-05
A few lines up, it also say that there is a problem with the RAMDISK (err=1).
I think ubuntu wanted to hibernate before it crashed. Is there any posibility to get ubuntu started without using the ramdisk?

---

### Post by SirIdefix on 2007-01-06
These are the last lines before the computer hang when I tried to boot it:

RAMDISK : Compressed image found at block 0
RAMDISK : Out of compressed data
invalid compressed format (err=1)
VFS cnnot open root device "hda2" or unknown block(0,0)
please append a correct "root=" option
Kernel panic - not syncing : VFS : Unable to mount root fs on unknown block(0,0)

---

### Post by SirIdefix on 2007-01-06
Could anyone help me, pleeaaase?
I know there were similar problems in previous threads.
But I do not have a second kernel installed. Also on my Ubuntu cd there is no
initrd.img .
Can someone tell me how I can get a working initrd.img file? 
The live cd works. Maybe with apt or something.

---

### Post by SirIdefix on 2007-01-06
I am very disappointed that nobody helped me even though I posted 4 times.
Here is how i got it working:
-> I started ubuntu with  a live cd (6.10 Edgy Eft).
-> I started the terminal
-> I mounted a new directory( ubuntu is on my hda2 partition)
```
sudo mkdir /tmp/dumpdir
sudo mount -t ext3 /dev/hda2 /tmp/dumpdir
sudo cd /tmp/dumpdir
```
-> I created a new ramdisk and copied it to the /boot folder
```
sudo update-initramfs -k 2.6.17-10-generic -c
sudo /tmp/dumpdir/initrd* /tmp/dumpdir/initrd.img-2.6.17-10-generic
```
-> then I restarted

---

### Post by Zamber on 2007-01-20
Thanks a lot for solveing this one. It happened to me 2 days ago, I had only a knoppix cd and had to download ubuntu install cd but after burning it and booting it was about 5 minutes to make it working ;D
I own you a beer ;)

---

### Post by nbayiha on 2007-02-03
thanks a lot SirIdefix you solve my problem to. i was going throw the same issue.:) 
thanks):P

---

