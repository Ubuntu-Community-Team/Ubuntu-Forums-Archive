---
title: "Black screen on Lubuntu 16.04"
date: 2016-04-25
forum: Hardware
---

### Post by Dertuny on 2016-04-25
Hi!! 

 I used Lubuntu without problems for a very long time, but now, with  the last distro update, I had a black screen and is impossible to go in system  normally. I tried a live usb with "nomodeset" option and runs normally, on update the system is absolutely dead, no grub, no screnn...but I don't like  this "strange" options to work with my pc...well, my machine is:

 

 - AMD A6-5400K GPU with
 

 - [AMD/ATI] Trinity [Radeon HD 7540D] (lspci says this)
 

 - MSI A68HM-P33 V2 Motherboard
 

 Previous version (15.10) worked very well. 

 

 I tried Arch based distros (arch, antergos, etc) and simply not boot,  I think for the same problem....I don't know if it's kernel, or X, or  drivers...
 

 Any suggestions?? I love Lubuntu and I will still using it!!!!

I'm looked to launchpad to report a bug, but I don't know how to do this, on Lubuntu section I can't find anything related to kernel or similar on the project selector.

Thank you!

---

### Post by ajgreeny on 2016-04-25
Are you trying to use the fglrx driver with that AMD card?

fglrx is deprecated in 16.04, at least for the moment, and you will have to use the amdgpu driver which should work better than the previous radeon.  I do not have any AMD hardware to test this problem, so this is all from non personal experience.

[https://wiki.ubuntu.com/XenialXerus/ReleaseNotes#fglrx](https://wiki.ubuntu.com/XenialXerus/ReleaseNotes#fglrx)

> **fglrx**

The fglrx driver is now deprecated in 16.04, and we recommend its open source alternatives (radeon and amdgpu). AMD put a lot of work into the drivers, and we backported kernel code from Linux 4.5 to provide a better experience.
When upgrading to Ubuntu 16.04 from a previous release, both the fglrx driver and the xorg.conf will be removed, so that the system is set to use either the amdgpu driver or the radeon driver (depending on the available hardware).

---

### Post by Dertuny on 2016-04-25
Yes, I readed this article, but, the verison have preinstalled packages radeon and amdgpu, and I don't know if is possible uninstall one of them to try, because it erases lubuntu-core package, and seems not a good idea....
I don't know too what is the way to try to solve this problem....

---

