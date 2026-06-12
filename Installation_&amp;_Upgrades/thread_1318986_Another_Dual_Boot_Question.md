---
title: "Another Dual Boot Question"
date: 2009-11-08
forum: Installation &amp; Upgrades
---

### Post by snailsonspeed on 2009-11-08
Hey guys and gals. I have recently installed Karmic on a dual boot with Winblows 7 being installed first. The 9.10 release was a clean install, and is using GRUB2 from what I understand. The install went fine, but when I reboot it bypasses GRUB and loads Windows always, while never giving me an option to boot an OS.

I have scoured this site, and have found similar precedence (the other way around Ubuntu installed first), but am unable to find my answer. I can see both partitions from the live CD, but can never have GRUB boot first. 

I hope I am not being redundant, but have honestly looked. So thanks in advance.

---

### Post by snailsonspeed on 2009-12-31
I know this is a bit old, but just in case anybody experiences a similar problem, I will elaborate my (admittedly stupid) problem.

If you are using dual(as I am) or more HDDs, pay attention to where Win 7 puts the MBR. In my case it installed on my slave, which for some reason was set to primary boot in the bios. 

Since it was looking to the slave drive on boot, it totally bypassed GRUB, booting straight to Windows.

I ended up wiping the drive, as I recently upgraded hardware, and have no problems loading Windows into Virtual Box, but if you have this problem, have a look at moving the Windows MBR to the primary drive.

---

