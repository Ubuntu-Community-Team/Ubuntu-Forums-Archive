---
title: "USB Drive Support"
date: 2005-01-20
forum: Hardware &amp; Laptops
---

### Post by digitalpure on 2005-01-20
I have a 20GB Maxtor drive that is on my USB 2.0 connections.  It is my backup drive for everything that I had in windows.  It is also where all my info is stored from my windows world.

I installed 4.10 last night, and LOVE it.  I am coming back to Linux after a 5 year stint in the windows world again, so I feel like a newbie...

I edited my etc/fstab/ to install the device under /mnt/usb0 with my permissions via uid=(username)  I can copy the EXACT fstab line later today when I can get back into the unit.  I am on my backup windows machine right now.  Here is what I remember

/dev/sba  /mnt/usb0  ntfs  rw,noauto,uid=digitalpure 0 0 (from my memory)

The drive is formatted as a single partition via NTFS....

Right now the system sees the drive, but when i try to mount it with nautlis or via terminal it gives me a "too many partitions active, or format problem"

If somecan tell me how it should that would be awesome.  I looked in the manual for warty and it looks similar to what I have.   I would like this to load on bootup, and have read/write access as I am the only user on the system.  

I can use gedit to modify my fstab as needed.

Thanks in advance, and I am 1000% glad that I found linux again.  I cannot believe how dumbed down windows makes a user.  I gotta start reading again, as i have missed alot.

If it helps here are the rest of my system specs
AMD 2500 Barton
512MB PC3500 DDR
MSI KT6-LSR Delta Mobo
200GB SATA HD (main drive)
20GB IDE HD (on USB 2.0)
Plextor Premium CD-RW
Plextor DVD-ROM
Audigy 2 Soundcard
19" Envision Monitor
MX1000 USB Laser Mouse

---

### Post by Viro on 2005-01-20
The problem is with the NTFS format. Linux doesn't support it out of the box. You need to download the following packages:

libntfs5
libntfs-gnomevfs
ntfsprogs

In order to download them, use either the Synaptic package manager or even easier, go to the console, and type
```

sudo apt-get install libntfs5 libntfs-gnomevfs ntfsprogs

```

---

### Post by digitalpure on 2005-01-20
thank you, I will try that when I get back to my box....  I will let you know if it works..

---

### Post by digitalpure on 2005-01-20
I installed the programs as suggested and am still having a issue...

Does anyone have a Warty installation running that has a USB drive working... can you send me the correct information that should be in my fstab line for this drive...

Here is the exact line out of my fstab:  the SDB is my USB drive.
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdc        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sdb        /mnt/usb0      ntfs    rw,user,noauto,uid=digitalpure  0       0
/dev/sdc        /media/usb1     auto    rw,user,noauto  0

---

### Post by digitalpure on 2005-01-21
ok, i got it to work... for some reason the system was looking for sdb1 even though the device manger said it was mounted on sdb... i added the fstab entry for sdb1 and now it works great

Now, if I had write access to the device it would be great.  I can only get READ access.. I did put the rw,auto,uid=digitalpure in the fstab and when i mount the device it shows i have ownership, just no write access...

i am copying everything over to my main system, and then i am going to format this drive with ext3 anyway, so no big deal.... unless someone has a good answer for me.

---

### Post by TaNeK on 2005-01-21
You _CAN_ get write permissons to NTFS, but it's almost sure to screw something up. If you can, change filesystem to reiserfs, or if you want to be able to read it under windows, go fat32.

---

### Post by Viro on 2005-01-21
[QUOTE=digitalpure]ok, i got it to work... for some reason the system was looking for sdb1 even though the device manger said it was mounted on sdb... i added the fstab entry for sdb1 and now it works great

Now, if I had write access to the device it would be great.  I can only get READ access.. I did put the rw,auto,uid=digitalpure in the fstab and when i mount the device it shows i have ownership, just no write access...

i am copying everything over to my main system, and then i am going to format this drive with ext3 anyway, so no big deal.... unless someone has a good answer for me.[/QUOTE]
 I'm glad you got it to work. On my Ubuntu installation, I didn't have to do anything to my /etc/fstab file. Just plug the drive in on my fresh install and it mounted(!!!). I think this has to do with udev, which is oh so cool.

For read/write NTFS in a reliable way, try installing the package called Captive-NTFS (can't check it, on a PPC Box) or something like that. It takes the Wine-like approach and uses the Windows NTFS driver on Linux to provide write support.

---

### Post by digitalpure on 2005-01-22
i actually hosed my system really badly last night, and now i reinstalled my whoel system....

i actually am copying all the contents onto my main drive, and then going to format teh system using ext3 -j so that it is a linux only backup drive.... i have decided that i am not going to use windows at all anymore...

i actually convinced my office to let me be one of 3 linux users in the office, so it will be nice to get 100% out of the windows world

thanks to everyone that helped, it is 1000% appreciated.... it nice to try and learn it on your own, but nicer to know there is someone there to help you when you got a problem.....

---

### Post by davegod75 on 2005-01-31
[QUOTE=Viro]I'm glad you got it to work. On my Ubuntu installation, I didn't have to do anything to my /etc/fstab file. Just plug the drive in on my fresh install and it mounted(!!!). I think this has to do with udev, which is oh so cool.

For read/write NTFS in a reliable way, try installing the package called Captive-NTFS (can't check it, on a PPC Box) or something like that. It takes the Wine-like approach and uses the Windows NTFS driver on Linux to provide write support.[/QUOTE]


hmm..wish that was the case for me...I have to manually mount my USB hard drive..and my kingston USB thumb drive won't mount at all

---

