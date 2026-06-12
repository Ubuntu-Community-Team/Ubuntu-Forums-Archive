---
title: "Ubuntu in a VM + SAN failure"
date: 2014-10-15
forum: Hardware
---

### Post by cpdondo on 2014-10-15
I had an interesting failure.  We run about a dozen VMs on a server, mostly Windows, one RH5, and one Ubuntu 14.04.  The server is connected to a SAN via what is supposedly redundant switches.  Last week the switches got a firmware update, and in the process dropped the connection from the VM server to the SAN.  (Apparently the failover isn't working, but that's not for here.)

The bottom line is that all of the Windows and RedHat virtual machines recovered fine, except for my Ubuntu 14.04 install. It saw the disk go away, and just stopped.  OK, not too bad.  On reboot, it came back with an "ext4 journal truncated" error and mounted / read only.

I had to go into recovery mode and manually run fsck on the machine, and now it's fine.

So my question is this:

Should I expect ext4 to act this way?

I can see 2 possible reasons for this:

1.  the EXT4 journal got corrupted and I was in danger of losing everything.
2.  the EXT4 file system saw something bad happened and refused to mount rw until a human being fixed the problem.

Of course, I'd much rather it was 2. than 1.

---

### Post by TheFu on 2014-10-15
You were lucky 2/3rds of the time. That's all.
Journaling is amazing. All modern OSes use it to make recovery after a failure just like this possible in fairly short order.

I would take the other VMs down this weekend (next maint window) and run fsck (or the equiv) on those as well.

---

