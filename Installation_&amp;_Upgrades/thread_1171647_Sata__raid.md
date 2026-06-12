---
title: "Sata / raid"
date: 2009-05-27
forum: Installation &amp; Upgrades
---

### Post by m3bik on 2009-05-27
I've recently tried installing Ubuntu Server 8.10 on a computer. The computer has two 80GB SATA hard drives. When doing the install, I see something about turning on the SATA RAID devices. If I click yes, I get an error message and have to go back. If I click no, the install continues. The two drives are listed in the partition screen. I set the drives like I wish and continue.

When I reboot the computer to start linux, I get an error message saying Error loading operating system. Then it asks for a boot CD/DVD.

Am I not configuring this right or do I need to upgrade to 9.04?

---

### Post by m3bik on 2009-05-27
I don't need RAID set up. I just need to install Ubuntu to one of the drives and keep the other one for storage.

---

### Post by orange-wedge on 2009-05-27
This sounds like a BIOS issue...  You may try re-installing grub or re-running the installation.

---

### Post by m3bik on 2009-05-28
The computer had XP on it and it booted fine. I haven't changed anything, but formatted it. If the BIOS booted from the hard drive with windows, why can't it boot from the same hard drive with linux?

---

### Post by m3bik on 2009-05-28
I've tried Ubuntu Server 9.04 and it installs with no errors, with or without RAID enabled.

With RAID enabled, I get the same boot problem.

With RAID disabled, the computer boots with no problems now. I haven't changed anything, just the version of Ubuntu. Either way, it looks like I've got the problem fixed. 

Thanks!

---

### Post by orange-wedge on 2009-05-28
Are you using software raid?

---

