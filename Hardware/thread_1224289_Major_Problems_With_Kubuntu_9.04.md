---
title: "Major Problems With Kubuntu 9.04"
date: 2009-07-27
forum: Hardware
---

### Post by Smoke.Static on 2009-07-27
Ive got a Toshiba A-215 with AMD Turion dual core.  I have had the APIC bug with every version of ubuntu 9.04.  The Kubuntu distro is the one I would like to use, but it fails to boot, that is without a workaround.  The live USB installed fine on my PC and other Acer notebook.  But when I tried to install it on the Toshiba, it gives me a FATAL modprobe error.  Since the Toshiba's hard drive died (I hate hitachi) i use an external USB HDD.  I installed the live USB onto that drive via the Acer.  Now, when I try to boot on the Toshiba, the same thing happens as when i boot the live USB.  After reporting the APIC bug, It says this:

modprobe: FATAL: Could not load /lib/modules/2.6.28-11-generic/modules.dep: No such file or directory

Then up pops the Kubuntu loading screen, that finishes, and it's back to the errors, where it aborts:

Loading, please wait...
Gave up waiting for root device.  Common problems:
- Boot args (cat /proc/cmdline)
  - Check rootdelay= (did the system wait long enough?)
  - Check root= (did the system wait for the right device?)
-missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/edb18b8c-864a-4e54-b880-6cb5e9777e3a does not exist.  Dropping to a shell!



BusyBox v1.10.2 (Ubuntu 1:1.10.2-2ubuntu7) built-in shell (ash)
Enter 'help' for a list of built in commands.

(initramfs)

/**
*when i try cat /proc/cmdline i get: root=edb18b8c-864a-4e54-b880-6cb5e9777e3a ro quiet splash
*
*also, the file mentioned in the modprobe error IS there and the path is correct.
*/

And here is the part where I unplug the HDD, plug it back in, and after i get the message:

(initramfs) [ 557.739614] sd 6:0:0:0: [sda] Assuming drive cache: write through
[  557.741114] sd 6:0:0:0: [sda] Assuming drive cache: write through  (it says it twice, is this because I have two partitions? actually 3 including swap)

and I type exit, then it boots.  it says: 
kinit: no resume image; go ahead with normal boot 
or something to that effect, and everything is fine.  I would really like to avoid all this just to boot up.  I apologize if this issue has already been solved, I could not find a solution that worked.  I would appreciate any help and/or suggestions.

Also, I'm having trouble with the APIC bug, connecting to a windows shared folder and installing the proper video driver.  When I installed the suggested driver for my x1200 it freezes while loading the desktop.  These are minor in comparison but I have searched for a recent solution to these as well and have come up with nothing that helps me.:confused:

---

