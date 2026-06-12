---
title: "Grub error 18: Selected cylinder exceeds maximum suported by BIOS"
date: 2008-11-29
forum: General Help
---

### Post by Angryhenrik on 2008-11-29
Hello all,

I'm getting the above error when trying to boot into Ubuntu.

To give a bit of context, I had the laptop running over night possibly running Transmission, when I came to use it this morning it was hanging, and generally being unresponsive. Turned the power off, and now I'm getting the above error.

Additionally trying to boot from the live CD so I could at least recover some data returns the following errors;

ata1.00 status (DRDY ERR)
ata1.00 error ( UNC )
Buffer I/0 error on device sda

Any help would be greatily Appreciated.

Regards

---

### Post by Angryhenrik on 2008-11-29
UPDATE: The liveCD eventually boots, but it doesn't seem to recognise the Hard Drive?

The laptop itself is an Acer Aspire 5920.

---

### Post by Bucky Ball on 2008-11-29
[http://users.bigpond.net.au/hermanzone/p15.htm#18](http://users.bigpond.net.au/hermanzone/p15.htm#18)

That gives an explanation of what is happening at least. I have no fix but you might get some ideas.

---

### Post by caljohnsmith on 2008-11-29
OK, how about opening a terminal (Applications > Accessories > Terminal) and please post the output of:
```
sudo fdisk -lu
```
From the above output, determine which is your Ubuntu partition in the form sdXY (like sda2 or similar) by noticing which partition is "linux" under the "system" category, and then use that as follows:
```

sudo umount /dev/sdXY
sudo fsck -y /dev/sdXY
sudo mount /dev/sdXY /mnt
nautilus /mnt &
```
Note the first "umount" command might give an warning that sdXY is not mounted; that's OK, it is only to make sure sdXY is unmounted. And the last command should allow you to browse your Ubuntu partition if all goes well. Please post the output of all the above commands and we can work from there if you want. :)

---

### Post by Angryhenrik on 2008-11-30
> **caljohnsmith said:**
> OK, how about opening a terminal (Applications > Accessories > Terminal) and please post the output of:
```
sudo fdisk -lu
```
From the above output, determine which is your Ubuntu partition in the form sdXY (like sda2 or similar) by noticing which partition is "linux" under the "system" category, and then use that as follows:


Thanks for the response.

Unfortunatley, I tried the first command, which didn't return an output, it just took me to a new line within Terminal.
I carried on with the second one anyway on the partition I'm fairly sure I installed Ubuntu too (from what I gather it's a disk check?). 

This outputs the following;

[I]/dev/sda3 contains a file system with errors, check forced

"Error Reading block #####" (Attempt to read block from filesystem resuled in short read) while getting next inode from scan.

Ignore Error? yes
Force rewrite? yes
[/I]
As I sit here it's currently going through innumerable blocks doing the above.

---

### Post by Angryhenrik on 2008-11-30
UPDATE: I'm now getting a message when booting the machine along the lines that the HDD is about to fail, so I think it's probably save to assume that's where my other problems originate from!

Anyway, most of the work is backed up, apart from two openoffice documents I'd like to recover before sending the drive off for replacement. 
The drive is listed as a SCSI drive, but nothing is accessible/is listed as unmountable.

Where would be a good starting point to try and recover the work?

---

### Post by mdurham on 2008-11-30
Sorry to hear about your disk problem Angryhenrik. I noticed that you said you were going to send the disk back somewhere, under warranty perhaps? Just remember to completely remove any sensitive info from it first, like bank account things, passwords etc. Sorry I can't help with fixing it though.
Cheers, Mike

---

