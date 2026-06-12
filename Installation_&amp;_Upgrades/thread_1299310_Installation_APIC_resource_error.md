---
title: "Installation APIC resource error"
date: 2009-10-23
forum: Installation &amp; Upgrades
---

### Post by dxer on 2009-10-23
I've downloaded the KUBUNTU 9.04 i386 image, burned to CD, and boot the target system. I select "English", then "Install Kubuntu", and then get a busy "Kubuntu" screen followed by:
 
[ 2.289438] IO APIC resources could not be alloacted.
Loading, please wait...
 
BusyBox v1.10.2 (Ubuntu 1:1.10.2-2ubuntu7) built-in shell (ash)
Enter 'help' for a list of build-in commands.
 
(initramfs)
 
Any help out there? I'm uncertain if I was dumped because of the APIC issue. The motherboard is about 8 yrs old, not sure what interrupt control structure it has.
 
dxer

---

### Post by Shazaam on 2009-10-23
Try this...
1. Re-burn the Ubuntu livecd as slow as possible- 2x if you have the time. Make sure you check the cd for defects.
2. IIRC you can hit F6 (or F4) at the livecd boot screen to change boot options.
3. Download and try the "Alternate Install" livecd. It may be called the mini.iso
4. Depending on your hardware specifications Xubuntu might be a better choice.
5. Search the site for initramfs/busybox errors.

---

