---
title: "reserved blocks: can they be reduced?"
date: 2008-09-01
forum: General Help
---

### Post by eeried on 2008-09-01
Hello,

When you install X/Ubuntu you can reduce the percentage of reserved blocks on partitions / and /home too.

I haven't found definitive information on how important reserved blocks are.

So I've set 2% for both / and /home (respectively Reiserfs and Ext3) instead of the 5% default. 

At least it saves quite some disk space.

Is this dangerous?

---

### Post by unutbu on 2008-09-01
The answer depends on how big your partitions are, and whether or not you run any processes as root that require a lot of writing to disk. 

Imagine this scenario. Your hard disk is full (except for the reserved blocks). You can't log in as a normal user, because the act of logging in writes to /var/log/auth.log but the disk is full. So you boot into recovery mode, which dumps you into a root shell. Root can log in because it can use the reserved blocks. An entry is written to /var/log/auth.log. The first act as root is to clean up trash, do apt-get autoclean, etc. Once you clean up some space, you are fine again.

On the other hand, suppose you were running a backup script as root which was in the middle of copying a big file to /tmp. Your hard drive fills up and even the reserved blocks are gone because it was root running the script. Now the computer starts spewing out strange errors, and probably halts. You can no longer reboot and log in because even root can not write to /var/log/auth.log (among other things). So what do you do? 

Easy. Boot from a LiveCD, mount your linux partition, and clean up some space from there. Again, once you clean up some space you are back in business.

The bottom line is, you probably need very little space for reserved blocks to allow root to log in through recovery mode. I am not an expert and have never read of an officially recommended amount for reserved blocks. However, it seems to me given the above scenarios, you would never need more than 100 MB of reserved space (and even that amount I've chosen mainly at random). 

Given the humongous size of modern hard drives the 5% default is way too much.
If you have a 100GB partition, 100MB is only 0.1%.

---

### Post by eeried on 2008-09-01
Many thanks for the information, unutbu.

I'm dealing with various kinds of computers but now I'm installing Xubuntu on an 8-ish HDD.

Yet I'm sure the users will never run out space or fill up the disk, and 2% on / should be enough.

On /home reserved blocks don't seem to be very useful, or are they?

---

### Post by unutbu on 2008-09-01
Yes. I agree, I can not think of any reason why /home needs any reserved space at all.

---

