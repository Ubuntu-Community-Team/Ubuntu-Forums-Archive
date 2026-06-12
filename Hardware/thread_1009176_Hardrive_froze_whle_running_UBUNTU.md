---
title: "Hardrive froze whle running UBUNTU"
date: 2008-12-12
forum: Hardware
---

### Post by mojo_man on 2008-12-12
Hi,

The other day I was running UBUNTU and all of sudden the hard drive froze. I have two hard drives--one for WINDOWS XP and one for UBUNTU. I assume since UBUNTU froze it must have been the UBUNTU drive that was acting up. Not sure where GRUB installed itself--I think the UBUNTU drive is the master one but not 100% sure. I am writing this at work and am not being lazy to look inside my machine ;-)

I used SMARTCTL command to look at the health of all the partitions on the drive and it said PASSED. In the logs for the UBUNTU drives there were errors reported (no error code but usually read access issues) 

After the drive froze when I rebooted the BIOS hung. So I tried again and got GRUB but got ERROR code 18. My research shows that a BIOS upgrade might be necessary to alleviate this problem BUT I do not see why given that this a new motherboard. 

Before I do anything drastic I should I should consult with this group. Some people say I should reinstall GRUB. I would just like to know why the hard drive just froze all of a sudden.

I ran fsck on the the linux partition and all is fine.

---

