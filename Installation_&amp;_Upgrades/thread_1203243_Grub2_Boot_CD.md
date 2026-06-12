---
title: "Grub2 Boot CD"
date: 2009-07-03
forum: Installation &amp; Upgrades
---

### Post by Narusegawa on 2009-07-03
I'm using 9.04 before someone asks.

I loaded grub-pc as per [https://wiki.ubuntu.com/KernelTeam/Grub2Testing](https://wiki.ubuntu.com/KernelTeam/Grub2Testing) however when going into "Chainload into Grub2" I just get

```
Welcome to grub!.
error: no such disk
```

I then get a grub recovery prompt, typing ls at this lists me

```
(hd0) (hd0,1) (hd0,2)
error: out of disk
```

hd0 are my ntfs drives, hd1 is where my ubuntu install is.

Typing root (hd1,3) tells me it's a ext2 fs. Yet ls refuses to list anything at all.

I'd really like to try Grub2 properly as my exact motherboard is listed as fully compatible on that list too. GA-P35-DS3. So... if I perform a 'real upgrade' to Grub2, is there a LiveCD or something I can use (easily preferably) to re-apply Grub1 from the default install?

I suspect Grub2 is having issues with core.img and that the Grub1 is loading from my first sata drive, but /boot is on the first partition of the second sata drive, and / is the 3rd on that same drive.

Yes, I know there is no need for a seperate /boot partition but I'm an old Gentoo user and thats just a habit now :(

---

### Post by ridgeland on 2009-07-04
Thanks for the link.  I read this thread before trying Grub2 for myself.  I use chainload and tested on a copy of Ubuntu 9.04 on a partition that I would not care if I lost.
It did not boot at first.  I keep menu.lst on /dev/sda1 and chainlink to almost all the Linux I install.  This copy of 9.04 is on /dev/sdb10.  It's a clone of /dev/sdb14.  When grub legacy displayed the menu I chainloaded to /dev/sdb10 where I had just installed grub-pc.  I selected the first option though I didn't understand it.  I got error 11.  From your post's link I knew to edit and change the root line.  I tried changing root to UUID and got garbage about /dev/sdb14.  I hate UUID but tried it anyway.  What finally worked was "root (hd1,9)".  Now I'll explore some more with grub.

On my old PC I keep a separate /boot because the BIOS will not boot anything past 4 GB.  I share the /boot with several distros.

Do you never get the second GRUB menu after chainloading from the first?

---

### Post by ridgeland on 2009-07-05
I'm back to grub legacy.  That was a rough ride.
I did learn how to create /etc/grub.d/11_personal and run /usr/sbin/update-grub to load it into /boot/grub/grub.cfg.
I did not get chainload to work.
I could not switch back to my previous grub legacy + menu.lst.  From the grub2 prompt "setup" is no longer recognized.  So booting was stuck on /dev/sdb10 not /dev/sda1 where I want it.
I could not find good documentation.  The grub2 manual is a passing shot of ideas and needs as much as instructions.
My solution to get back to grub legacy was to install Ubuntu 9.04 fresh to another partition (/dev/sdb11).  This installs grub legacy to the master boot record and grub> setup gets me back how I want it.
Once that was done the partition with grub2 is not unaccessible!  I can no longer get to /dev/sdb10.  Good thing that was a throw-away partition.

Only bright side is I did verify Grub2 on my Dell Deminsion E520n and add that PC to the list for the Grub2Testing team.

---

