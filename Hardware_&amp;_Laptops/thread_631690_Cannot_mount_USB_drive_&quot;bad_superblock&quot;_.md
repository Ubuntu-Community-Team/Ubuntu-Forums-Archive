---
title: "Cannot mount USB drive &quot;bad superblock&quot; / &quot;VFS: Can't find a valid FAT filesystem ..&quot;"
date: 2007-12-04
forum: Hardware &amp; Laptops
---

### Post by SJWackness on 2007-12-04
Good day mates.

I'm posting on behalf of my friend who's gotten himself into a bit of a muddle.

He has an external USB drive (500g Western Digital) which stopped working one day while he was using XP.  Every time he plugs it in, Windows insists the drive is without a format and thus, must be formatted.

I've run into similar problems while using XP and always managed to boot into Linux, mount the drive, copy the files to another drive, and reformat.  So, that's what I had resolved to do for him.

The problem is that I can't get the drive to mount in Ubuntu.  I'm using a Live CD on his laptop (which is without internet, so I can't  just copy and paste the error messages) to try and access the drive.  This is what I get in response:

---
ubuntu@ubunut: sudo mount -t vfat /dev/sda1 /mnt/
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
missing codepage or helper program, or other error
In some cases useful info is found in syslog - try
dmesg | tail or so
---
ubuntu@ubuntu: dmesg|tail
FAT: bogus number of reserved sectors
VFS: Can't find a valid FAT filesystem on dev sda1
---
ubuntu@ubuntu: cfdisk /dev/sda
sda1     primary      W95 FAT32      (LBA)     500105.25
---
ubuntu@ubuntu: sudo hdparm -iI /dev/sda1

/dev/sda1
HDIO_GET_IDENTITY failed: Invalid argument
HDIO_DRIVE_CMD(identify) failed: Invalid argument

-----------------------------------------
When I run "sudo hdparm -iI /dev/hda1" everything comes up as one would expect.

So, where does this leave us?  Is the drive completely rubbish now, or is it possible to bring it back up?  If memory serves me correctly, I had a similar problem that I was able to resolve by doing something as simple as an MBR fix.

Please, I'm open to all suggestions.

Cheers.

---

### Post by fmonjaraz on 2008-05-23
Did you fix your problem? I am having the same issue.

---

