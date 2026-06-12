---
title: "Erased My Hard Drive!!!!"
date: 2007-11-05
forum: Hardware &amp; Laptops
---

### Post by gatorsdb22 on 2007-11-05
Earlier today I downloaded Ubuntu onto a CD. I was running off of Vista. I downloaded the ISO file onto a CD. When I put in the CD to try to download it and run the install, a partition screen popped up. I honestly had no idea what I was doing, so I changed around the ext3 to ext2 and stuff like that. I kept getting and error message. So I gave up. I pulled out the disc and restarted my computer to try to get back onto Vista.I kept getting a screen that said "Err22, Err23" or something like that. I took it to the IT guys here at my college and they said they think I erased all my Vista stuff. Is that true? I have a paper on there that is due this Friday!!! I need it back asap if it's possible! Please help! Thanks so much!!!

---

### Post by wieman01 on 2007-11-05
All you could try is to boot from Ubuntu Live CD and try to mount the Vista partition, then copy the file in question over to your harddrive. But I cannot promise this'll work as you might have indeed erased the file system. In that case you are in trouble.

When you boot from Live CD, please open a terminal and post the output of this:
> fdisk -l
This will tell you what partition are left and recognized by the system. We will try to mount it thereafter.

---

### Post by gatorsdb22 on 2007-11-05
How do I open a terminal? I'm sorry, I just have NO idea what I'm doing...

---

### Post by wieman01 on 2007-11-05
I don't use the same GUI as you (I use KDE, not Gnome), so I cannot tell you exactly where it is. But one of the menu items should say "Terminal" or something like that. Just click it and it would open a **command line** window. So should be able to find it.

---

### Post by aj61779 on 2007-11-05
Applications menu to
Accessories menu to
Terminal

---

### Post by gatorsdb22 on 2007-11-05
So I need to restart Ubuntu and run it from the opening screen?

---

### Post by gatorsdb22 on 2007-11-05
Ok I did that and this popped up....

Usage: fdisk [-l] [-b SSZ] [-u] device
E.g.: fdisk /dev/hda  (for the first IDE disk)
  or: fdisk /dev/sdc  (for the third SCSI disk)
  or: fdisk /dev/eda  (for the first PS/2 ESDI drive)
  or: fdisk /dev/rd/c0d0  or: fdisk /dev/ida/c0d0  (for RAID devices)
  ...
ubuntu@ubuntu:~$

---

### Post by wieman01 on 2007-11-05
Did you type... "fdisk -l"? 'l' like "language".

---

### Post by gatorsdb22 on 2007-11-05
Well at first I had just typed in the "fdisk" but when i typed in fdisk -l nothing came up....

---

### Post by wieman01 on 2007-11-05
Nothing came up? Oh... I think that's pretty bad news in fact.

All you do is search on the web for data recovery programs or something like that. I am afraid there is nothing we can do about it right now. If "fdisk" does not list any partition, it's probably gone.

---

### Post by FXEF on 2007-11-05
Type sudo fdisk -l

---

### Post by gatorsdb22 on 2007-11-05
Well when I just typed in "f-disk" the following came up....

Usage: fdisk [-l] [-b SSZ] [-u] device
E.g.: fdisk /dev/hda (for the first IDE disk)
or: fdisk /dev/sdc (for the third SCSI disk)
or: fdisk /dev/eda (for the first PS/2 ESDI drive)
or: fdisk /dev/rd/c0d0 or: fdisk /dev/ida/c0d0 (for RAID devices)
...
ubuntu@ubuntu:~$

came up. But when I typed in "f-disk -l" nothing did. But above you can see it automatically put the "-l" in brackets....

---

### Post by gatorsdb22 on 2007-11-05
Ok. When I typed in "sudo fdisk -l" this came up....

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x546edcf4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          31      248976   82  Linux swap / Solaris
/dev/sda2              32        2463    19535040   83  Linux
/dev/sda3            2464       19457   136504305    b  W95 FAT32
ubuntu@ubuntu:~$

---

### Post by FXEF on 2007-11-05
Simply type: sudo fdisk -l

Then post the results.

---

### Post by wieman01 on 2007-11-05
> **FXEF said:**
> Type sudo fdisk -l
Oh, you are right. You saved our day, mate. :-) Confused it with RescueCD.

To mount the device, do this:
> sudo mount /dev/sda3 /mnt
Done that?

---

### Post by gatorsdb22 on 2007-11-05
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x546edcf4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          31      248976   82  Linux swap / Solaris
/dev/sda2              32        2463    19535040   83  Linux
/dev/sda3            2464       19457   136504305    b  W95 FAT32
ubuntu@ubuntu:~$

---

### Post by gatorsdb22 on 2007-11-05
Ok. When I typed that in, I got this....

ubuntu@ubuntu:~$ sudo mount /dev/sda3 /mnt
mount: you must specify the filesystem type
ubuntu@ubuntu:~$

---

### Post by wieman01 on 2007-11-05
Ok, try this:
> sudo mount -t vfat /dev/sda3 /mnt
Now open Nautilus, the file browser and navigate to this folder:
> /mnt
Do you see your Windows file system?

---

### Post by gatorsdb22 on 2007-11-05
Ok. It said this....

ubuntu@ubuntu:~$ mount -t vfat /dev/sda3 /mnt
mount: only root can do that

---

### Post by FXEF on 2007-11-05
You will need to mount the /dev/sda3 partition to see if your files are still there.

Type sudo mount -t vfat /dev/sda3 /mnt

---

### Post by wieman01 on 2007-11-05
Sorry again... forgot the "sudo" prefix:
> sudo mount -t vfat /dev/sda3 /mnt
Then fire up the file browser and go to "/mnt". Your files should be there.

---

### Post by gatorsdb22 on 2007-11-05
Ok. When I typed that in I got this...

ubuntu@ubuntu:~$ sudo mount -t vfat /dev/sda3 /mnt
mount: wrong fs type, bad option, bad superblock on /dev/sda3,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

### Post by wieman01 on 2007-11-05
> **gatorsdb22 said:**
> Ok. When I typed that in I got this...

ubuntu@ubuntu:~$ sudo mount -t vfat /dev/sda3 /mnt
mount: wrong fs type, bad option, bad superblock on /dev/sda3,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
The file system is definitely there, but perhaps it's been corrupted.

Anybody else with a smart idea?

---

### Post by gatorsdb22 on 2007-11-05
So the good news is that everything ISN'T erased? Any idea on how to get it back?

---

### Post by wieman01 on 2007-11-05
> **gatorsdb22 said:**
> So the good news is that everything ISN'T erased? Any idea on how to get it back?
Yes, I think the stuff is still there, but your HD has been "bruised" somehow. All I can do is bump this up and hope somebody smart joins in with a bright idea. :-( Sorry, I cannot help further.

---

### Post by wieman01 on 2007-11-05
Ok, this might help:
> sudo fsck /dev/sda3
It will ask you a bunch of questions... What is the first one?

I found that solution [here]("http://www.linuxquestions.org/questions/linux-hardware-18/mount-wrong-fs-type-bad-option-bad-superblock-on-devhdc3-373428/").

---

### Post by gatorsdb22 on 2007-11-05
I'm getting this when I type it in....

ubuntu@ubuntu:~$ sudo fsck /dev/sda3
fsck 1.40.2 (12-Jul-2007)
Floating point exception (core dumped)
ubuntu@ubuntu:~$

---

### Post by jabeez on 2007-11-05
hey if he was using Vista, would that explain the mount -vfat error? Vista uses NTFS.....

---

### Post by wieman01 on 2007-11-05
> **gatorsdb22 said:**
> I'm getting this when I type it in....

ubuntu@ubuntu:~$ sudo fsck /dev/sda3
fsck 1.40.2 (12-Jul-2007)
Floating point exception (core dumped)
ubuntu@ubuntu:~$
Ok, that's as much as I can do.

Anybody?

---

### Post by jabeez on 2007-11-05
another option would if you've gotta speedy internet connection and an extra cd would be to download and burn a good utility live cd distro, I've personally had good luck with Knoppix, it usually recognizes and mounts all your drives/partitions...............

---

### Post by wieman01 on 2007-11-05
> **jabeez said:**
> hey if he was using Vista, would that explain the mount -vfat error? Vista uses NTFS.....
"fdisk -l" says FAT32 though.

Yes, a good Rescue CD would be this one:

[http://www.sysresccd.org/Download]("http://www.sysresccd.org/Download")

---

### Post by az on 2007-11-06
> **gatorsdb22 said:**
> So the good news is that everything ISN'T erased? Any idea on how to get it back?

If you need data recovery tools use this:

[http://ubuntu-rescue-remix.org/](http://ubuntu-rescue-remix.org/)


However, if you have internet access from the Ubuntu live cd, you can use that.

Stop playing around with your partition immediately!  Image it and try to fix the image - that means your write every bit into a file and work on the file instead of the actual drive.  For example, you can try the ntfsfix tool from the ntfsprogs package. 

If that doesn't work, you can possibly mount it using ntfsmount (that's different than actually mounting it and you may have some success even if the filesystem is borked.)  If that still fails, you can data-carve your documents out of there.

---

### Post by wieman01 on 2007-11-06
> **az said:**
> Stop playing around with your partition immediately!
A day ago or so I would have said that's a fairly obvious advice, but apparently it isn't always... ;-)

---

### Post by gatorsdb22 on 2007-11-07
I donwnloaded that SystemRescueCD onto a CD from someone else's computer. However, I put it into my computer and the plain black screen saying "Err22" still comes up. What do I need to do to get the CD to start working the program?

---

### Post by IcemanV9 on 2007-11-07
You may want to make sure the CD and ISO image are good by using md5sum.

```
md5sum <whatever the name>.iso
md5sum /dev/cdrom <-- make sure it's the correct device on your or someone else's PC
```

FWIW, it did happened to me a couple years ago. I used SLAX to rescue all my important docs/pix/data from unbootable WinXP partition to a blank CD. Then, I installed Hoary (5.10) to continue my work without losing a beat.

Don't give up until you can get your data off with rescue CD.

---

### Post by TubaTodd on 2007-11-08
> **gatorsdb22 said:**
> I donwnloaded that SystemRescueCD onto a CD from someone else's computer. However, I put it into my computer and the plain black screen saying "Err22" still comes up. What do I need to do to get the CD to start working the program?

Is your machine even TRYING to boot from CD? You need to enter the BIOS setup or the boot device menu and TELL your computer to try booting from CD first. It sounds like either...

a. You have a useless CD (any one of a bunch of different reasons why)
b. Your computer is NOT trying to boot from CD and it's trying to boot straight to the HD. (remember the Vista boot kept saying Err22)

If you can boot your Ubuntu CD....then choice a. is probably true. In any event....

Have you tried seeing if the files on the Vista partition are viewable? From the Ubuntu CD Click "places" then "home" This will bring up the file manager. On the left you should see your Vista partition towards the bottom of the list. It might be something like "/dev/sda1" or something like that. If you can click on it and VIEW the files on the right....then that is a "quick and dirty" way to see if your files are still there. 

My advice would be if you can see that Vista partition, hook up an external hard drive or some other backup device and start dragging your files to that device. Use the system restore disk that came with your machine (providing you have such an animal) and rebuild your machine. 

Of course....my REAL advice would be to back up those files and install Ubuntu....but I don't think that is what YOU wanted to do. :)

Good luck.

---

### Post by Mondoman on 2007-11-08
I'm guessing that the OP's computer originally had the Vista (and any recovery) partitions right at the start of the drive.  From the partition list the OP posted, there are now the Ubuntu swap and system partitions at the start of the drive.  My guess is that the OP's original Ubuntu changes ended up overwriting any recovery partition, and the the first part of the Vista partition, with the Ubutu partitions.  The 3rd partition reported, the FAT32 one, may either be a truncated remnant of the original Vista partition, or something created during the Ubuntu partitioning.  The errors associated with trying to access that 3rd partition suggest to me that it's a damaged truncated remnant of the original Vista partition.  If my general impression is correct here, and the OP did not have a very full disk, the OP's documents were likely in the area overwritten by the Ubuntu partitions and are now lost.

---

