---
title: "mount/fstab issue"
date: 2009-08-31
forum: Installation &amp; Upgrades
---

### Post by tor.tovsland on 2009-08-31
I added a 1TB hdd to my ubuntu server, created a partition and file system.
The new disk shows up as /dev/sdd1.
I then created a directory '/misc' where I want to permanently mount it.
When I do a 'mount /dev/sdd1 /misc' everything looks good, I can do a 'df' and it shows up, I can do a 'ls -l /misc' and it lists it. But when I add to /etc/fstab

UUID=bcf975f4-2cbb-4154-877f-64809032c118 /misc           ext3    realtime        0       2
 
and do a 'mount -a' I get the following:

mount: wrong fs type, bad option, bad superblock on /dev/sdd1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

What is wrong?
Filesystem was created by running 'mkfs -t ext3 /dev/sdd1'

---

### Post by tgeer43 on 2009-09-01
Get ready to blush. It's a simple typo.

It should be 'relatime' instead of 'realtime'.

Happens to the best of us. :wink:

tgeer

---

