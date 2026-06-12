---
title: "Ubuntu 8.04 distro upgrade to 8.10 problem (after install)"
date: 2009-06-18
forum: Installation &amp; Upgrades
---

### Post by KBD20 on 2009-06-18
Hi, recently I upgraded 8.04 to 8.10 (via online upgrade).
while it was installing, it had many errors (exit code 1, and exit code 2).
after I restarted it and it fully booted up, the screen looked all fuzzy and my mouse or keyboard didnt work, I think this is a hardware driver problem, On the boot process I noticed an error saying "Can't start hardware abstraction layer. please ensure dbus is running"
I think the solution to this is backing up everything using rsync onto a portable hdd and doing a fresh install. then rsyncing back
However, what I cannot figure out how to do is how to send the files to the portable hard drive as I can only work via terminal, the drive is formatted to ext 3 and its type (ie manufacturer) is imation.
Please post any advice for this, or any other that may help me.
Thanks in advance.

---

### Post by sanemanmad on 2009-06-18
How is this drive attached? USB i assume. then you will need to mount the drive to a location in say /mnt/something then proceed to use rync command line tools.

Read this guide. [Mount USB]("https://help.ubuntu.com/community/Mount/USB")

---

### Post by sanemanmad on 2009-06-18
In short...

```
sudo fdisk -l
```
and 
```
lsusb
```
identify the drive as /dev/sdb or similar.


```
sudo mkdir /mnt/usb
```

change the perm so you can write to it with out root privileges
```
sudo chmod 777 /mnt/usb
```

Change sdb with whatever the usb drive is.
```
sudo mount /dev/sdb /mnt/usb
```

---

### Post by KBD20 on 2009-07-06
Thanks for the help.
Now that I have backed everything up onto my portable hard drive and upgraded to 9.04, I cant seem to get all my files back over.
Also, the (portable) hard-drive is in ext3, same as my file system, when I backed everything up it was 110 GB of data, the portable hard-drive now says it has around 100GB used up and when I go to properties within the portable hard drive (top directory within it) it says a couple of hundred Mb (as apposed to the 100 or so GB that the portable drive says it has used up)
Could this mean there was a problem with my backup?
if you have any solutions to this, or know of any good data recovery software (to recover lost or deleated data).
Thanks again in advance. 
Also is using the rsync -av command safe for backing up in the first place?

---

### Post by sanemanmad on 2009-07-13
Hi KBD20,

Yes rsync is great for backing up data, however you should have also used the r switch,```
rsync -avr
```

rysnc -a [archive] v [verbose output] r [recursive] also you would want to exclude the mount location of the usb drive. If you did not use the r switch then that will explain why there is only a couple hundred megs vs gigs.

Hope this helps

---

### Post by KBD20 on 2009-07-13
Would that mean that I have lost most of my data if I have just used rsync -av that I have lost most/all of my data?
If so, do you know of any good data recovery software for Ubuntu or Livecd? 
Any good idea what the chances are of getting data back from a reformatted hdd (from upgrading to 9.04). (still ext3 like previous versions).
Again, thanks in advance 
:wink:

---

