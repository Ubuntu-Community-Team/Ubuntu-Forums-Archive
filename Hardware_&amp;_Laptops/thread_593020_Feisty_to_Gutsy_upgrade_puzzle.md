---
title: "Feisty to Gutsy upgrade puzzle"
date: 2007-10-26
forum: Hardware &amp; Laptops
---

### Post by ddmiller on 2007-10-26
Summary:

I just upgraded from Feisty to Gutsy, using the handy "Upgrade" button in the update manager.  Everything went smoothly, except my two non-boot hard drives, previously /dev/hdb and /dev/hdd became /dev/sdb and /dev/sdc, respectively.  This necessitated some minor tweaking of /etc/fstab to get access to my data again, which was no big deal.  But I'm curious - why the change?  Anyone have any insight?

Details:

I'm a relatively new Ubuntu (and Linux) user, but have experience with UNIX and Windows dating back 20 years (much more Windows in recent years than UNIX, alas).  I installed Feisty on a mongrel PC to serve as a backup machine.  This machine had /dev/hda, a 40GB PATA drive that came with the box, as the boot drive for Feisty (Ubuntu's the only OS installed - no dual boot here!).  /dev/hdb was the "slave" HD on the first IDE channel.  The DVD drive was the primary on the second IDE channel, and /dev/hdd was the slave on the secondary IDE channel.

I decided this afternoon to upgrade as described above.  After the expected amount of downloading and configuring, the system rebooted, and dumped me into a maintenance shell with a message that s2fsck had failed because it couldn't find /dev/hdb1.

I wasn't able to fix the problem in the shell (mainly because I'm rusty enough that I knew only a few basic commands to try), so hit CTRL-D to get out of it and go ahead to boot into Gutsy.  Once in Gutsy, I started GParted, which was when I noticed the /dev/sdb change.  A quick edit of /etc/fstab to change /dev/hdb1 to /dev/sdb1 and /dev/hdd1 to /dev/sdc1 fixed the problem.

So, I'm back in business, but I'm wondering why the change?

Thanks in advance for any insight ...

---

### Post by ddmiller on 2008-03-15
I did finally figure this out, and thought I'd post the reason in case anyone stumbles across this and wonders.

It has to do with the new kernel in Gutsy.  Apparently, the new kernel thinks that SATA drives are the norm, and hence uses /dev/sd<n> instead of /dev/hd<n>.

---

