---
title: "Unable to write to USB memory stick"
date: 2005-11-13
forum: Hardware &amp; Laptops
---

### Post by bartc on 2005-11-13
I recently bought an [Emtec USB memory stick]("http://www.emtec-group.com/page.asp?idRub=2&idSousRub=208&idSSRub=27"). It worked fine, but then I somehow managed to screw the partition table (maybe I unplugged it without unmounting it first?). Without any further thoughts I decided to start over with a clean disk, and zeroed the entire disk, using ```
dd if=/dev/zero of=/dev/sda
```

It seems like that was a rather bad idea... I can't write a new partition table on the disk now because I'm unable to open it with write permission. When I run parted I get the following output:```
bart@baobab:~$ sudo parted /dev/sda
Warning: Unable to open /dev/sda read-write (Read-only file system).  /dev/sda
has been opened read-only.
Warning: Unable to open /dev/sda read-write (Read-only file system).  /dev/sda
has been opened read-only.
GNU Parted 1.6.21 with HFS shrink patch 16
Copyright (C) 1998 - 2004 Free Software Foundation, Inc.
This program is free software, covered by the GNU General Public License.

This program is distributed in the hope that it will be useful, but WITHOUT ANY
WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A
PARTICULAR PURPOSE.  See the GNU General Public License for more details.

Using /dev/sda
(parted)

```
Running fdisk results in the following output:```
bart@baobab:~$ sudo fdisk /dev/sda
You will not be able to write the partition table.
Device contains neither a valid DOS partition table, nor Sun, SGI or OSF disklabel
Building a new DOS disklabel. Changes will remain in memory only,
until you decide to write them. After that, of course, the previous
content won't be recoverable.

Warning: invalid flag 0x0000 of partition table 4 will be corrected by w(rite)

Command (m for help):
```
The memory stick doesn't have a write protect switch, so that can't be the problem.
Has anyone got any advise?
thanks

---

### Post by metoo on 2005-11-13
I always use cfdisk for partitioning:
sudo cfdisk /dev/sda

try /dev/sda1 too, as some sticks might have a strange setup.

(make sure, that /dev/sda is not already mounted, unlikely)
umount /dev/sda

You are sure, that the stick is /dev/sda ?
Delete all partitions and create a new one. Use write before exiting, otherwise the stick will not be updated.
After re-partitioning you need to format the drive a new.
mkfs.vfat -F 32 /dev/sda

for a FAT32 filesystem.

---

### Post by kelsey23 on 2005-11-13
$sudo su

$umount /dev/sdb1

$mkdir /media/usb

$mount -t vfat -o rw,umask=0000 /dev/sdb1 /media/usb

$exit

---

### Post by bartc on 2005-11-13
cfdisk gives the same error message as fdisk.
I'm pretty sure /dev/sda is right, and it is not already mounted. I can't delete any partitions because there is no partition table! The problem is that I can't make a new partition because I can't write to the disk.

---

### Post by maltje on 2005-11-15
How can I see what partition my usbstick is???

---

### Post by bartc on 2005-11-16
[QUOTE=maltje]How can I see what partition my usbstick is???[/QUOTE]
Go to *System* > *Administration* > *Disks*
Select the USB stick from the *Storage list*, and take a look at the *Partitions* tab

---

### Post by maltje on 2005-11-16
/dev/sdb1
windows virtual fat
acces path  /media/usbdisk-1
So what now??


In hoary was it no problem.
Please help

---

### Post by bartc on 2005-11-16
[QUOTE=maltje]/dev/sdb1
windows virtual fat
acces path  /media/usbdisk-1
So what now??


In hoary was it no problem.
Please help[/QUOTE]
I'm afraid I don't understand what your problem is...
What are you trying to reach?

---

### Post by maltje on 2005-11-16
I try to explain :
I formatted (why I don't know anymore)my usb stick on a friends computer with windows XP.
No on my laptop I have breezy installed.
I put my usbstick in and I have the window with my usbstick.He is empty.
I copy some files and pasted them onto the usbstick.
In the window of my usbstick I see the files.
When I take out the usbstick there are NO FILES on it!!!
I don't understand it anymore.
I tried to copy and paste in nautilus as root,but stil the same problem.

When I do dmesg I get a lot of text,also this

VFS: Can't find a valid FAT filesystem on dev sdb 
Is this maybe the problem??
no filesystem on the stick!!

---

### Post by dcast on 2005-11-16
I had a similar problem try either save the files to the usb stick or  use the cp command

---

### Post by polo_step on 2005-11-16
This is an interesting thread.  

I've been thinking of using USB flash/jump/whateverdrives to move stuff between my Linux and XP systems (until I get up the courage to face setting up a Samba share), and had planned to pick up some cheap on Black Friday next week.  I was wondering how much of a nosebleed they'd be to use in Linux, as nothing seems to be terribly simple.

A tutorial on the "right" way to approach this from the start would be great.

---

### Post by maltje on 2005-11-16
[QUOTE=dcast]I had a similar problem try either save the files to the usb stick or  use the cp command[/QUOTE]

Thats the problem!!!
I cant get any files on the stick!!!!!

---

### Post by maltje on 2005-11-16
[QUOTE=polo_step]This is an interesting thread.  

I've been thinking of using USB flash/jump/whateverdrives to move stuff between my Linux and XP systems (until I get up the courage to face setting up a Samba share), and had planned to pick up some cheap on Black Friday next week.  I was wondering how much of a nosebleed they'd be to use in Linux, as nothing seems to be terribly simple.

A tutorial on the "right" way to approach this from the start would be great.[/QUOTE]

In hoary I never had problems with it.
Also I formatted the usb stick in XP,maybe that was not so smart.

---

### Post by VicVega on 2005-11-16
Have you tried to re-format from Ubuntu?

Vic

---

### Post by maltje on 2005-11-16
[QUOTE=VicVega]Have you tried to re-format from Ubuntu?

Vic[/QUOTE]
what is the command to format?
And format what?
sdb1??

---

### Post by VicVega on 2005-11-16
I am new to linux, so I'm not sure how to do it with the command line. I am not sure of the best way to do it, but I believe that you could use GParted for this. It is available in System > Administration > Synaptic Package Manager.

HTH

Vic

---

### Post by yuri6312 on 2005-11-17
ye  i have similar problem 
but i have no idea for solving it.
that's like a problem.

---

### Post by bartc on 2005-11-17
Maltje, try to reformat your memory stick using GParted. Next, try to paste some files on it, and then **unmount** the partition before you unplug the device. I guess that might have caused your problem.
I hope you're still able to partition the drive, unlike me ;(
I still haven't found a sollution yet. I hope to receive an e-mail from Emtec soon...

---

### Post by maltje on 2005-11-17
[QUOTE=bartc]Maltje, try to reformat your memory stick using GParted. Next, try to paste some files on it, and then **unmount** the partition before you unplug the device. I guess that might have caused your problem.
I hope you're still able to partition the drive, unlike me ;(
I still haven't found a sollution yet. I hope to receive an e-mail from Emtec soon...[/QUOTE]

When I unmounted it ,it is ok8
BUT,I never had to do this before!!
I installed gparted,but when I do sudo gparted in a console,nothings happends.

---

### Post by maltje on 2005-11-18
Here is what I did today:
I installed qtpated,this works.
I put some files on my stick and then unmount it.Wait for a few seconds then pull out the stick.
I got an error :no device.... so I think I have to leave the stick a longer time after unmount?!
I put some file on the stick in XP without any problems.
But when I play them I here also old music.
Back home I put the stick in the computer with ubuntu and delete all the files.
Then I go to "show heddne files" and try to delete them also but now I got the error:not possible to delete a read only file??!!
I tried this also as root.
Please can anybody helps me?
ICould it be a bug in ubuntu breezy?
:(

PS.After I unmount the usbstick take him out,put him back in,I can't find him anymore!!

---

### Post by webwolf_27 on 2005-11-18
say has anybody thought of just formatting the USB-stick instead of repartitioning it? if the device is /dev/sdb then run mkfs -t vfat /dev/sdb on the UNMOUNTED usb-stick.

Hope this Helps

webwolf

---

### Post by maltje on 2005-11-18
mkfs.vfat 2.11 (12 Mar 2005)
/dev/sdb: No such file or directory

---

### Post by webwolf_27 on 2005-11-18
maybe try mkfs.vfat /dev/sdb1

webwolf

---

### Post by maltje on 2005-11-18
[QUOTE=webwolf_27]maybe try mkfs.vfat /dev/sdb1

webwolf[/QUOTE]

nope same problem.
How can I see what it is,sdb1 or something else?

It has to be sda
but....
mkfs.vfat: Will not try to make filesystem on full-disk device '/dev/sda' (use -I if wanted)

---

### Post by maltje on 2005-11-24
Still the same problem
Nobody for a solution?

---

### Post by maltje on 2005-11-24
I installed ubuntu 5.10 again.
I didn't do any update.
But the problem with the usbstick is still there.
I got /media/usbdisk with files ,but on the usbstick there aren't any files!!!
I unmount the stick and when I put him back in,I don't get it on my desktop!!
What a problems!!!!
At this moment all the rest is just working fine.
Do I have to mount him in /etc/fstab or something like that??

---

### Post by metoo on 2005-11-24
plug in the stick
open console
sudo umount /dev/sdb
sudo umount /dev/sdb1
***just to be sure***
sudo cfdisk /dev/sdb

This should give you an overview of the partitions on the stick. Could be more than 1! 

You can delete any partitions and re-create 1 big new one. Make sure, that you select the right file system type (LBA 95 or vfat for Fat32).
After writing the new partition table, you have to format the stick again:
sudo mkfs.vfat -F 32 /dev/sdb
for a fat32 file system.

When using cfdisk and mkfs.xxx better be sure, that the device specified is your stick! :-)
Keep in mind: some sticks have a write protection slider!

---

### Post by maltje on 2005-11-24
I think it has to be sda
but when I do
sudo umount /dev/sda,i get sda not mounted!

---

### Post by maltje on 2005-11-25
Strange:
When I unmount the stick and I wait a few minutes and then I pull it out the usb,then the files are on the stick!!
WHy have I wait so long?
I test it once,hopefully it works always.

---

### Post by topic58 on 2005-11-25
I have got that problem on my USB-stick too. But with a friend I think we solved the problem. We mounted the stick in Ubuntu 5.10 - it came up okay - then umount by right-click the icon. Open GParted - right-click on the USB-stick sd-something - convert to vfat (FAT32) or whatever you want it in (NOT FAT16). Then let the USB-stick mount by connecting it. That's it! Did it for me. Does this help out?

---

### Post by maltje on 2005-11-25
[QUOTE=topic58]I have got that problem on my USB-stick too. But with a friend I think we solved the problem. We mounted the stick in Ubuntu 5.10 - it came up okay - then umount by right-click the icon. Open GParted - right-click on the USB-stick sd-something - convert to vfat (FAT32) or whatever you want it in (NOT FAT16). Then let the USB-stick mount by connecting it. That's it! Did it for me. Does this help out?[/QUOTE]

last time gparted didn't work but I used qtparted.Hopefully I can choose fat32the last time that wasn't in the list.

Let the USB-stick mount by connecting it:What do you mean with this?
And do I have to do it every time?

---

