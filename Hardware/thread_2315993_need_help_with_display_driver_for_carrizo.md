---
title: "need help with display driver for carrizo"
date: 2016-03-04
forum: Hardware
---

### Post by safknw on 2016-03-04
I recently bought new laptop Lenovo Ideapad 500-ACZ, it has A10-8700P processor. I installed Ubuntu 15.10, I installed fglrx-updates using hardware driver utility, I believe it is latest version. When I try to open Catalyst control panel, it crashes with segfault.

Since AMD is working on new open source driver amdgpu ( I guess it will be feature complete in kernel 4.5), so I'm curious if fglrx does not support Carrizo family APUs?
I'm planning to user later 4.5 kernel (currently rc6), please confirm if this is correct approach

1. Install kernel as specified here [http://www.yourownlinux.com/2016/03/how-to-install-linux-kernel-4-5-rc6-in-linux.html](http://www.yourownlinux.com/2016/03/how-to-install-linux-kernel-4-5-rc6-in-linux.html)
2. Install amdgpu driver from Padoka ppa ([https://launchpad.net/~paulo-miguel-dias/+archive/ubuntu/mesa](https://launchpad.net/~paulo-miguel-dias/+archive/ubuntu/mesa)).

I never tried development version of kernel, so little doubtful if it is correct approach. 

One more question if I only install latest amdgpu driver from Padoka ppa, will it be enough?

---

### Post by QDR06VV9 on 2016-03-04
@safknw Sadly you are correct they are as dicribed below..

> AMD APU series codenamed &#8220;Kaveri&#8221;, &#8220;Godavari&#8221; and &#8220;Carrizo&#8221; are only supported by AMD Radeon Software Crimson Edition Beta  on Windows® 7 (32 & 64-bit), Windows® 8.1 (64-bit) and Windows® 10 (64-bit).

---

### Post by safknw on 2016-04-01
In install 4.5 rc6, but it didn't helped much, will try again with kernel 4.6.

---

### Post by nukedathlonman on 2016-05-06
If your using 15.10, then fglrx should work with out issue using the latest and greatest in the Ubuntu (non-PPA) repo's.  I've been running Kubuntu on my Carrizo (A10-8700P) with that driver with out any issue at all since I bought my Pavilion in Dec.  But 16.04 doesn't support the latest Crimson drivers, which mean's you'd have to use the open source driver (AMDgpu).  It semi works, but for me randomly kicks out (the screen will randomly blank or go black).  I can ssh into my machine to shut it down that way, or I can suspend the system and resume it and it will work for a short bit after.  I know for sure it's not a DPMS thing, and I have opened a bug report on this.  I myself am going to go back to 15.10 tomorrow when I'll have the time to restore my back up.

---

### Post by nukedathlonman on 2016-05-06
Interesting - that looks like the current Windows Crimson disclaimer...  Actually it's not quite - because they added a disclaimer to Crimson 16.3.x and after that some Carrizo listed products aren't supported at all (and what they list, is only every single last "Carrizo" released to date - so "Carrizo" actually isn't supported by the current Windows drivers at all regardless of release (16.2.1 was the very last Windows Crimson edition with "Carrizo" support on Windows - but don't panic, apparently there was some sort of bug discovered by QA that's caused the removal of support and it's supposed to be resumed at some unspecified future date).  But on the Ubuntu 15.10 side, I've had zero issues (not even with the control panel) with the latest Crimson from the standard repo's.

---

### Post by QDR06VV9 on 2016-05-06
Thanks for sharing nukedathlonman... i would suspect this thread will be looked at a little bit with this new information.
Kind Regards

---

