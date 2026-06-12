---
title: "mount error and other funny stuff"
date: 2013-04-23
forum: Hardware
---

### Post by Acradon on 2013-04-23
Hi, 

about a  year ago I bought an extra harddrive and mounted it successfully with some help in the forum here. I edited the fstab and everything was good. 
About a week or so ago some funny stuff started happening. The new hard drive suddenly appeared to be read only. I thought that was odd, since I didn't change anything. But I put it off to deal with it later. The next day everything was back to normal. a week later it happened again, this time it persisted through numerous reboots. OK, I deal with it later I thought. And today the volume does not mount anymore at all. I tried changing the fstab a little. My main hard drive (boots the OS and contains all programs etc.) showed the mount options: 

rw,user,noauto,exec,utf8 0       0 

while the one with the problem showed

defaults

So I mimicked the main drive option since that hard drive seemed to be OK.

I rebooted and couldn't even get past the bios. I couldn't enter the setup menu or the boot menu. Funny stuff. I unplugged the hard drive with the problem to make sure that there are no conflicts in trying to boot the system now, to no avail. However, while I was trying to think of another option and was sorting through my CDs to look for a live CD the computer suddenly (after 2-3min) went past the bios and started to boot. 

So what is going on???

I still don't have my storage hard drive plugged in because I don't want to reboot before knowing what the problem is. Before I disconnected the problematic drive I checked the disk using the disk utility menu. Haven't run fdisk yet either. 

Any ideas?

Thanks 

Acradon.

---

### Post by dabl on 2013-04-23
Using a Parted Magic or GParted Live CD or USB stick, boot the computer and fsck the drives.  Note any errors found by fsck.  Then reboot the computer and post back if there are still issues.

---

