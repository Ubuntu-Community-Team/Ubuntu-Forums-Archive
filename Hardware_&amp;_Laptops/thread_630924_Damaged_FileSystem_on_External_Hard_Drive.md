---
title: "Damaged FileSystem on External Hard Drive"
date: 2007-12-03
forum: Hardware &amp; Laptops
---

### Post by OpIvy on 2007-12-03
Here's the situation.  I was upgrading the hard drive in my server, which is running Ubuntu Server.  Both the new and old hard drive were 'ext3'.  I got the new hard drive in place and was copying the files from the old one to the new one via a USB external enclosure.  The transfer had begun and was going smoothly when it suddenly the server lost the connection to the USB hard drive.  

I tried to remount the hard drive and got this error

      [I]mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so[/I]

I then took the hard drive to my laptop running Ubuntu.  When I plug it in it gives me an error about a corrupted filesystem and that its unable to mount it.

I need help.
There were 250 GB of music and movies on there that I need recoverd.  There is no physical damage to the hard drive.  It was sitting in one place and just lost connection.  Is there any way to get my data back?

---

### Post by zekopeko on 2007-12-03
try running fsck on it. read the manual for more info on fsck. and the drive has to be unmounted for fsck to work

---

