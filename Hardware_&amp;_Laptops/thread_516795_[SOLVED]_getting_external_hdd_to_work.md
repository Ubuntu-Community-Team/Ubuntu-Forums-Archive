---
title: "[SOLVED] getting external hdd to work"
date: 2007-08-03
forum: Hardware &amp; Laptops
---

### Post by Ffuzzdaddy on 2007-08-03
i have a seagate 60 gb external drive it is formatted for fat32, and when i plug it in nothing happens.
 i can use a usb memory stick and Ubuntu detects it perfectly, but nothing happens when i plug in the external drive.

---

### Post by Ffuzzdaddy on 2007-08-07
any help would be greatly appreciated

---

### Post by Ffuzzdaddy on 2007-08-14
bump

---

### Post by XTREEM|RAGE on 2007-08-15
Some more info plz about your system. Do you dualboot etc?

---

### Post by Ffuzzdaddy on 2007-08-15
i am on a laptop , it is a fresh install, no dual booting.
intel dual core, ati x1600 mobility radeon

---

### Post by kyphi on 2007-08-15
Some USB powered external hard drives require two USB connections.  You should be able to feel the vibrations as it spins.  If you can't then the device is not getting enough power.

---

### Post by bliffle on 2007-08-15
I've done that on my thinkpad T40 running feisty when I put a HDD in a box connected to the USB2 port, and it worked when the HDD was already formatted. For example, I put an old Windows system HDD in the box and it came up fine for read-only access. i had to add read/write capability for NTFS to be able to write.

Now I'm trying to get an unformatted HDDgoing in a USB box, and i think I have to mount the aw HDD in the T40 first and format it there (I'm doing this at this moment), then, I hope, I can put it in the box for external use.

I have a topic in this forum called "HDD Utility?"

---

### Post by Ffuzzdaddy on 2007-08-15
yea i have both usbs plugged in, the light comes on and it i can feel it spinning. but nothing pops up,  is there a command for me to type in to have it detected?

---

### Post by kyphi on 2007-08-15
You could create a mount point for the external drive.  There are excellent HowTos at:

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows) (with particular reference to FAT32)

[http://ubuntuforums.org/showthread.php?t=283131&highlight=automount+usb+devices](http://ubuntuforums.org/showthread.php?t=283131&highlight=automount+usb+devices)

You might also consider reinstalling  1. dbus  2. hal  3. pmount using synaptic, although a fault there seems unlikely since you can automount other USB devices.

Good luck.

It is always a good idea to state your version of Ubuntu

---

### Post by Ffuzzdaddy on 2007-08-21
i am running fiesty, i tried making a mount point and when trying to mount it i got this message

wrong fs type, bad option, bad superblock on /dev/sdb,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

i am new to ubuntu so i dont know what this means

---

### Post by christofer on 2007-08-21
it's a bug in fiesty, I tried updating HAL from the backports but that did nothing for this problem. I only use my WD Mybook on Dapper, it seems to work perfect. Only problem with Dapper is you can't upgrade the kernel without it potentially messing up your system. I sure wish they would fix these problems, it is getting old. Microsoft is starting to look good again.

---

### Post by Ffuzzdaddy on 2007-08-22
well that doesnt help at all

---

### Post by Ffuzzdaddy on 2007-08-25
so there is no way of getting my information off of my hdd?

---

### Post by markusr on 2007-08-28
hi

i have the same problem...


i solve it like this:

created a static mount point for the usb drive:
for example

sudo mkdir /media/usb

then mount it manually every time i need to access it... haven't found out how to automate this yet

sudo mount /dev/sdb1 /media/usb -t vfat

this command can differ depending on what filesystem you have at the usb drive, how the usb hd is partitioned, and what you harddisks are like

for all i found out ubuntu create a /dev/sdX device if you connect the usb drive, where X is the first free device

for me its b - because i have a sata hd working
for anyone without sata and so on....

the command may be

sudo mount /dev/sda1 /media/usb -t vfat

---

### Post by Marat Galiev on 2007-08-28
this command is wrong.
try this
[B]mount -t vfat /dev/sdb1 /media/usb

[/B]

---

### Post by Ffuzzdaddy on 2007-08-28
i was able to make the mount point, but when i tried mounting it nothing happened. should i use vfat, because the hdd is formatted to FAT32. thanks for your help

---

### Post by markusr on 2007-11-05
nothing happened?
if nothing happens - the disk usually was mounted :)

or did an error occur?

---

