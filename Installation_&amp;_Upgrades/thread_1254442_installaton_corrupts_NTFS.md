---
title: "installaton corrupts NTFS"
date: 2009-08-31
forum: Installation &amp; Upgrades
---

### Post by JaminIan on 2009-08-31
When I use Wubi to install, the install says all went well, but ubuntu won't boot and then the uninstall fails because the NTFS partition is corrupt.
 
My system:
AMD x64, WinXP SP3, (real) Hardware RAID (managed in BIOS - windows only sees mirrored device), Plenty of RAM and free space in the partition (> the 11Gb I want to allocate to Ubuntu)
 
Steps I took:
- run Wubi with pre-downloaded 9.04 x64 iso and select to install to D:
- the Wubi wizard completes successfully and I select to reboot immediately
- after the reboot I select Ubuntu from the boot menu
- the automated system runs, saying it's checking the install and so forth.
- the automated system reboots
- I select Ubuntu from the menu again, and I'm dropped into Grub
- Grub is unable to find any install  (gives options to "find ......", but all options fail)
- select reboot
- choose Windows at the boot menu
- attempt uninstall of Wubi
- uninstall fails with vague error
- need to run chkdsk with auto fix option about 3 or 4 times before NTFS partition is clean enough to uninstall Wubi.
 
I've gone through these exact steps 3 times now, and get exactly the same result each time.

---

### Post by ronparent on 2009-08-31
If the wubi install cd is like the ubuntu live cd, it is not equipped with software to install to raid drives. Thus the ntfs partition will appear corupted - it could be worse if it were raid0. I think the following reference could walk you thru it: [B][https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
[/B]
 
Basically it will show you how to install raid support for the cd session to enable an install to a raid device. Post your result and will try to help if you have problems.

---

