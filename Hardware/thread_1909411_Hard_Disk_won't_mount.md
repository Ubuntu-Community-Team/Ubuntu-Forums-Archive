---
title: "Hard Disk won't mount"
date: 2012-01-15
forum: Hardware
---

### Post by cscomp3 on 2012-01-15
Recently, upon boot, we saw a BIOS message that something was wrong with the hard drive.  Then when Ubuntu attempted to load from the hard disk, we recd this message:

mount: mounting /dev/disk/by-uuid/cc8a9ae1-66cf-45d8-9d7b-f470f3169342 on /root failed: Invalid argument
mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init.
No init found. Try passing init=bootarg.

BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)

I found this thread:

[http://ubuntuforums.org/showthread.php?t=1788381](http://ubuntuforums.org/showthread.php?t=1788381)

After reading it, I made a bootable CD from Ubuntu with 10.04 LTS.  Then when it booted from CD, I ran this in the terminal

e2fsck -f -y -v /dev/sda1

Did not help.  Then I checked the hard drive through the booted Ubuntu and found it was listed as /dev/sda, so I ran this in the terminal:

e2fsck -f -y -v /dev/sda

Nothin'.

So then I made a bootable USB stick from Slax, but, despite trying all the BIOS tweaks I could see, I could never get the machine to actually recognize and boot from the USB stick.

I have not tried making a Slax bootable CD.  Football came on . . .

Help!  We have a lot of pics stored in the machine and we, as usual, have not backup up in a while.  I think the disk is retrievable and repairable, I just don't know how yet.

Assistance is much appreciated to get this disk back working.

And what is "BusyBox"?

Thank you.

cscomp3

---

### Post by BC59 on 2012-01-15
You cannot access to the drive booting from a LiveCD?

---

### Post by cscomp3 on 2012-01-15
That sounds interesting like I have not tried it.  However, by LiveCD, do you mean the 10.04 LTS bootable CD I made?  and what do you mean by "accessing the drive booting"?

Sorry for the newbie ignorance here.  The system has run so well for so long, I have not had to dive into this for a while.

Thanks.

---

### Post by cscomp3 on 2012-01-15
And the machine is on 10.04 LTS, not 9.10 Karmic.  Need to update my profile.

cscomp3

---

### Post by BC59 on 2012-01-15
You can burn an .iso file to a CD, from any Ubuntu version.
Then boot from the CD and when you reach the screen Try or Install, choose try.
Wait a little bit to finish and then you have a system working from the CD. Just search from there for your files and make a backup.

---

### Post by cscomp3 on 2012-01-15
O.K.  We are on the same page.  That is what I did first.  I could find the drive as /dev/sda, but Ubuntu said there was no data on the disk.  It's like there is no "FAT" table or the Linux equivalent.

---

### Post by cscomp3 on 2012-07-13
Never could get the disk to work.  I have just decided I have hardware failure, found another disk and installed 12.04LTS.

Thanks, All.  cscomp3

---

