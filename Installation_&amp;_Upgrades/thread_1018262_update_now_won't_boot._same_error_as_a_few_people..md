---
title: "update now won't boot. same error as a few people."
date: 2008-12-21
forum: Installation &amp; Upgrades
---

### Post by danlutz on 2008-12-21
Ok I've seen the post before but after trying all the things I read still having the same issue.

Could someone walk me though a fix for the issue.

I'll start from the top

1st thing
as soon as I do the reboot after I finish the install I get this
> [0.004000] Aperture beyond 4G. Ignoring
[0.004000] Your BIOS doesn't leave a aperture memory hole
[0.004000] Please enable the IOMMU option in your BIOS setup
[0.004000] This cost you 64 MB or ram

Then it goes to the ubuntu studio splash screen. Seem fine but then errors out

> Boot from (hd0,4) ext3 6eecd30d-c4dc-49c2-b099-2a8066b7c1a5
Starting up...
[0.004000] Aperture beyond 4G. Ignoring
[0.004000] Your BIOS doesn't leave a aperture memory hole
[0.004000] Please enable the IOMMU option in your BIOS setup
[0.004000] This cost you 64 MB or ram
Loading, Please wait...
Gave up waiting for root device. Common problems:
-Boot args (cat /proc/cmdline)
 -Check rootdely= (did the system wait long enough?)
 -Check root= (did the system wait for the right device?)
-Missing modules (cat /proc/modules; ls /dev)
Alert! /dev/disk/by-uuid/6eecd30d-c4dc-49c2-b099-2a8066b7c1a5 does not exist. Dropping to shell!

BusyBox v1.10.2 (Ubuntu 1:1.10.2-1ubuntu6) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)

I know it has to do with Grub and setting my partitions.
I have windows install also but tried it with a full formatted disk and I still get the same issue. 
Need some help
Thanks.

My system info if I run sudo blkid
> /dev/sda1: UUID="F8944CD5944C9850" TYPE="ntfs" 
/dev/sda2: UUID="28A843C0A8438AF0" TYPE="ntfs" 
/dev/sda3: LABEL="M-;M-^O^SM-BmM-;sM-sM-B^M-'" UUID="48AC-E43E" TYPE="vfat" 
/dev/sda5: UUID="6eecd30d-c4dc-49c2-b099-2a8066b7c1a5" TYPE="ext3" 
/dev/sda6: TYPE="swap" UUID="d5150585-cf71-4614-a490-c696044dc8d9"
 

Also  I can boot into ubuntu if I edit one of he lines in the grub menu. Add _rootdely=130_ to the end of the text. But want to fix the issue right if I can.

---

### Post by danlutz on 2008-12-22
Well now adding rootdely=130 doesn't work. just get the error I posted above.
If I just put8.04 back on will that fix the problem.
Please need help
haha

---

### Post by danlutz on 2008-12-22
anyone

---

### Post by SlidingHorn on 2008-12-22
Please wait 24-48 hours before "bumping" a thread.  This forum is community-based and there just may not be anyone capable or with the time available online at this time.

Please be patient :)

---

### Post by sirdrakey on 2009-01-03
have the same problem boots just fine on my other computer but my faster build would load and i get the 

> [0.004000] Aperture beyond 4G. Ignoring
[0.004000] Your BIOS doesn't leave a aperture memory hole
[0.004000] Please enable the IOMMU option in your BIOS setup
[0.004000] This cost you 64 MB or ram 

when I am trying a fresh start with the live cd

my problem is how do you edit a kernel on a cd that is not installed yet

everyone says just add pci=nomci but how do i do that!!!!:popcorn:

---

