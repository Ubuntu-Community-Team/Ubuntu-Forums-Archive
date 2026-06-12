---
title: "Upgraded to 9.10 and cannot boot"
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by suryasaha on 2009-10-31
Hi, 

I upgraded to 9.10 from 9.04 using the update manager. The upgrade finished with some minor errors that have been filed in launchpad
446863       package python-telepathy 0.15.11-1 failed to install/upgrade
463729     package libxml-sax-perl (not installed) failed to install/upgrade    
467639     py_compilefiles crashed with SIGSEGV in getfilesize()

The system showed that it had upgraded to 9.10 with some problems and will run "dpkg -a ???". However, it did not reboot. The dpkg was not among the active processes (usnig top) after a few minutes. I ,rather foolishly it seems, went ahead and rebooted the computer manually. Now on bootup, I get

Grub loading....stage1.5
Error 15: file not found

This takes me to a boot menu that looks like 
Kernel name
Kernel name (recovery mode)....

However, on selection of any option, The Error 15: file not found reappears. 

My file system is ext2, if that matters. I would like to fix this installation of 9.10 or at least roll it back to 9.04. The file system is fine since a 9.04 live CD can access my files fine. 

Thanks in advance for help.

-Surya

---

### Post by suryasaha on 2009-11-02
If anybody else has the same problem, there is a fix here
[https://wiki.ubuntu.com/Grub2#Error%2015%20-%20File%20not%20found](https://wiki.ubuntu.com/Grub2#Error%2015%20-%20File%20not%20found)

Grub legacy was not updated to grub2. This fix requires the 9.10 live CD and installs grub2 on MBR. I had to install grub2 using apt-get before I could apply to the MBR.

```
apt-get install grub-pc
```-S.

---

