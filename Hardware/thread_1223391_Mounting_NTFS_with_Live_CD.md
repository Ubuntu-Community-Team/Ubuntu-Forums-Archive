---
title: "Mounting NTFS with Live CD"
date: 2009-07-26
forum: Hardware
---

### Post by awhirr on 2009-07-26
Hi

I am trialling Ubuntu 9.04 using a Live CD.

The PC has Windows XP installed.

I would like to be able to mount the NTFS drive but have failed so far.  Is this not possible using the Live CD?

This was what I tried.....

[I]ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbc57bc57

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19457   156288321    7  HPFS/NTFS

ubuntu@ubuntu:~$ sudo mount -t ntfs-3g /dev/sda1 /media/windisk

NTFS signature is missing.
Failed to mount '/dev/sda1': Invalid argument
The device '/dev/sda1' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
ubuntu@ubuntu:~$ [/I]

The big issue may be that the disk is encrypted.  I was hoping that as part of the mounting process I would get the chance to type in the user name and password but have searched various forums to no avail.  Theoretically I could take the encryption off of the drive but don't want to do that if there is a work around within Ubuntu.

Thanks for any help with this.

Matt

---

### Post by IcarusR on 2009-07-26
If the drive is encrypted & you can temporarily remove encryption to test Ubuntu cd why not do so. 
Probably less chance of data getting corrupted that way.

---

### Post by IcarusR on 2009-07-26
Googling & reading more you need to use a program called ntfsmount. 
I do not believe ntfsmount is part of the standard Ubuntu install, therefore probably not part of the live cd.
I do not know if one can install programs when using live CD. 
For sure if it is possible they will only be available during that session, ie no longer available after reboot.

So my previous suggestion may be the best solution.

---

### Post by awhirr on 2009-07-26
Thanks for your advice.  Removing the encryption does make it all work but is not something I want to do long term.

I looked at ntfsmount but it only seems to deal with encrypted files and not whole disks.

I guess that's the point of the encryption.

---

