---
title: "CDROM problem on VAIO laptop"
date: 2007-01-02
forum: Hardware &amp; Laptops
---

### Post by Sha-baz on 2007-01-02
Hi there,
 
I'm having trouble mounting my CDROM on my VAIO latop for some time now.
The CDROM was recognized at some time, because I installed from it. There is nothing wrong with the device, it works fine under Windows.
 
Here's the thing:
[img]http://o.foto.radikal.ru/0701/c25e9344c925.jpg[/img]
 
When I double click on this CDROM icon, the following appears:
[img]http://k.foto.radikal.ru/0701/64a50a98ace6.png[/img]
 
And finally: here's the content of my fstab file:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3
UUID=f820fe85-bdc0-4a55-9554-a8f0b3466f81 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda6
UUID=97a9a5be-5d25-445f-8e95-e00d31b020ab none            swap    sw              0       0
/dev/hdb        /media/cdrom    auto 	user,noauto     0       0
/dev/hda1	/windows/c      ntfs    umask=000   0 	0
/dev/hda5	/data           vfat    umask=000   0 	0

```
 
Does anyone know what's wrong here?

---

### Post by tommcd on 2007-01-02
Usually, the cdrom drive is listed like this in fstab:
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
Perhaps you could try that in your fstab. First, back up your fstab:
'sudo cp /etc/fstab /etc/fstab.bak'
Then do 'gksudo gedit /etc/fstab' and change your /dev/hdb to that. 
Also, make sure you have a directory titled /media/cdrom0 in your /media directory.

---

### Post by Sha-baz on 2007-01-02
I know, I changed 'udf,iso9660' for 'auto' to try to fix this problem, but it still exists. I'll change it back.
The mountpoint exists, no worries there.
 
Could this be a compatibility issue?

---

### Post by Sha-baz on 2007-01-02
The funniest thing is: the entire device does not show up in my dmesg output.
How could this be?

---

### Post by tommcd on 2007-01-02
I suppose it could be. When you first boot up do you get errors with:
dmesg | grep hdc
I'm not sure what to make of the output if you do get errors. A few days ago I was getting I/O erors with this, and my cdrom was working fine. Usually, however, I get this:

tom@ubuntu:~$ dmesg | grep hdc
[17179572.800000]     ide1: BM-DMA at 0xff08-0xff0f, BIOS settings: hdc:DMA, hdd:pio
[17179574.104000] hdc: LITE-ON DVDRW SHW-160P6S, ATAPI CD/DVD-ROM drive
[17179574.784000] hdc: ATAPI 48X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(66)
tom@ubuntu:~$

---

### Post by Sha-baz on 2007-01-02
dmesg | grep hdc gets me absolutely nothing.
dmesg | grep hdb says this:
```
[17179573.824000]     ide0: BM-DMA at 0x1810-0x1817, BIOS settings: hda:DMA, [COLOR="Red"]hdb[/COLOR]:DMA
```
 
And that's the only proof of 'hdb' in there...

---

### Post by Sha-baz on 2007-01-02
Well, I opened my laptop to take a look at the machine... This is some info about it:
[IMG]http://o.foto.radikal.ru/0701/a18bc811a00e.jpg[/IMG]
 
One thing that I noticed was the connection, is this even IDE?
[IMG]http://o.foto.radikal.ru/0701/79a87a129e4d.jpg[/IMG]

---

### Post by Sha-baz on 2007-01-02
I tried re-installing Ubuntu 6.10 but the problem remains. Even at the last phase of the installation, when Setup asks you to click OK to open the tray and remove the CD, the CDROM responds nicely by opening up. After the reboot the fun is over and the device doesn't 'exist' anymore...

---

### Post by Sha-baz on 2007-01-08
Problem solved. If anyone who reads this has the same problem, find your sources.list file and replace the word 'edgy' for 'feisty' to make Kernel 2.6.20 available in your package manager. Upgrade your Kernel.

This problem occured on my VAIO FS215B laptop, which had a Pioneer DVR-K15 dual layer CD/DVD writer. This writer is not recognized by Kernel 2.6.17 and older. This is a known bug.

---

