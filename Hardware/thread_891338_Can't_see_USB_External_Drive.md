---
title: "Can't see USB External Drive"
date: 2008-08-16
forum: Hardware
---

### Post by jpeery on 2008-08-16
I think I've got a drive going south, I hear it spin up, and it lights up, but I don't ever see it mount.  A little lost in what to do, is there a disk utility I can use to try to recognize and potentially fix the drive (given there's no physical damage to it)?
Thanks!
JP

---

### Post by wilbbe01 on 2008-08-16
Has it mounted automatically before?

---

### Post by cdtech on 2008-08-16
With it plugged in type (in a terminal):
```
sudo fdisk -l
```
See if we can see it.

---

### Post by jpeery on 2008-08-16
Looks like it's only seeing my HDD:

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x90da4431

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14242   114398833+  83  Linux
/dev/sda2           14243       14593     2819407+   5  Extended
/dev/sda5           14243       14593     2819376   82  Linux swap / Solaris


This is a USB (with it's own power supply) 500 GB WD, my friend's.  He says it shows up on his box but he can't access anything on it.  From what I can tell my (Ubuntu) laptop doesn't even see it.  Of note, it does power up, and shows green in the circle (if you're familiar with these WD drives).  In other words, it APPEARS to spin up ok and have power...
Thanks,
Jason

Oh yeah, never automounted on this laptop, but is the first I've tried...

---

### Post by cdtech on 2008-08-16
It's definitely not showing up in Ubuntu. The only other option I can suggest is to use "gparted", but I can almost guaranty it wont show up under there either. Do you know what's on the drive (ie: windows, linux)?

---

### Post by jpeery on 2008-08-16
I want to say it's an NTFS, I know my friend is running XP, so I (dangerous as it is) ASSUME he formatted it NTFS.
Here's what I get outta parted:

(parted) print

Disk /dev/sda: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system  Flags
 1      32.3kB  117GB  117GB   primary   ext3         boot 
 2      117GB   120GB  2887MB  extended                    
 5      117GB   120GB  2887MB  logical   linux-swap        

(parted)      

Thanks for the help guys, I'm at least learning a lot!
Jason

---

### Post by cdtech on 2008-08-16
If it is indeed plugged in then "sudo fdisk -l" would have shown the device as "sdb". You might try other USB slots to be sure.

Sorry.........

---

### Post by jpeery on 2008-08-16
Yeah, that's what I think, now I have to tell my friend 500GB of movies and songs are gone.  Maybe I'll start with: "A priest, the President and Elvis walk into a bar..."
Thanks again,
JP

---

### Post by cdtech on 2008-08-16
:lolflag:

---

### Post by wilbbe01 on 2008-08-16
If you can get into the enclosure you could always try taking the drive out and plugging it in internally.  You never know if the little board with the drive has a broken usb port or something.

---

### Post by jpeery on 2008-08-16
I've been told you could do that (take them out of the case and use them internally).  I am building a new box for said friend, perhaps I'll put this drive in it and see what happens.
Thanks again,
JP

---

