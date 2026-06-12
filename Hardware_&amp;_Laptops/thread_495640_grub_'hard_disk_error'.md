---
title: "grub 'hard disk error'"
date: 2007-07-08
forum: Hardware &amp; Laptops
---

### Post by ian_o on 2007-07-08
After install on my laptop grub reports 'hard disk error' when attempting to boot.

A little research suggested starting the boot on the live cd, then selecting 'boot from 1st hard disk' which works perfectly.  Research has also suggested that the problem is that the hardware as reported by the bios does not match the actual drive spec. There is a suggestion to upgrade the bios which has not solved anything.
Given that grub can actually work- although right now it needs to be launched with the intermediate step of the live cd-  there must be some config setup that allows it to proceed directly?  Does anyone have any suggestions?
I tried the /boot/grub/device.map file as a candidate and renaming it did change anything so it is not contributing.
It has 
(hd0)	/dev/sda
as the only contents.

Any suggestions as to how i can configure things to eliminate the live CD step greatly appreciated!!

---

