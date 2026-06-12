---
title: "NTLDR Missing After Ubuntu Install - XP Won't Boot"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by Octanum on 2009-10-30
Basically, what I did was install Ubuntu Netbook Remix 9.10 and now XP won't boot claiming NTLDR is missing. I guess I'll go through the process of what I did and maybe someone can see a problem.

I first used UNetbootin to copy the contents of the iso to a flash drive, due to the fact that my HP Mini 110-1030CA has no DVD/CD drive. I started up using the flash drive and partitioned my disk as follows: 1st Partition was NTFS for Windows, 2nd Partition was ext4 for Ubuntu, and 3rd Parition was swap for Ubuntu.

During the install process, I went through the normal prompts, and when it came time to set mount points, I selected partition two as my mount point, and partition 3 as my swap area. At the end, it told me that both of these partitions would be formatted. In the advanced section at the end of the install, I recall seeing the path GRUB would install to as "/dev/sda" or something along the lines.

So far, I've installed desktop versions of Ubuntu multiple times in the same way and have never had a problem, but for some reason, the netbook version decided to break everything.

Also, I should probably mention that it detected XP as "Windows Vista (loader) (on /dev/sda1)" for some unknown reason.

Any help with this issue would be much appreciated. I'd normally use the XP disk to restore, but seeing as I don't have a copy of XP Home laying around and that this was an OEM install, I'm somewhat stuck.

Edit: Also, I mounted my XP partition from Ubuntu and I see that NTLDR still exists.

---

### Post by Octanum on 2009-10-30
Alright, so I basically gave up on fixing it without the CD. I used my XP Pro SP3 CD which I use on another computer and copied it to a flash drive using WinToFlash. Just booted into recovery console, ran fixboot, and everything performed perfectly, even though this was an XP Home installation.

Kudos to that program as well, even made my flash drive bootable! :)

---

