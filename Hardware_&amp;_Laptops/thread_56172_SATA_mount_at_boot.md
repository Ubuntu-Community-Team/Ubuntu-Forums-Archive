---
title: "SATA mount at boot"
date: 2005-08-11
forum: Hardware &amp; Laptops
---

### Post by One Quick Question on 2005-08-11
Ubuntu can't find /dev/sda1 at boot. I can mount it fine manually after I've logged in and everything is user-y, but it can't do it automatically when it mounts the ATA drives.
And in case you're wondering, my fstab file goes something like this
```
[... blah blah blah, lots of drives in the file ...]
/dev/hdg1       /mnt/hdg1 reiserfs user,acl        0       2
/dev/sda1       /mnt/sda1 reiserfs user,acl        0       0
[... and a few more ...]
```
And if its pass parameter isn't 0, it gets really confused and wants to go into maintenance mode.
I'm sure where to look in /var/log to find the boot log, but on boot it says something simple like /dev/sda1 not found.
So how do I make it detect the SATA drives earlier?

---

### Post by One Quick Question on 2005-08-13
I was finally able to figure it out.  I will post the (a? my?) solution here in case anyone else has similar problems.

What I did was add ata_piix to /etc/modules.
That's all.

I found the information [here](http://ubuntuforums.org/archive/index.php/t-30233.html) and tested them all until I got something to work.

Next up:  How to get it to mount 6 partitions of 834 GB faster :-P

---

