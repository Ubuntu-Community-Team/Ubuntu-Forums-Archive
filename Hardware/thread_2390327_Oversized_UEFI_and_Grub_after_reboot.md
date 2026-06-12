---
title: "Oversized UEFI and Grub after reboot"
date: 2018-04-27
forum: Hardware
---

### Post by spectatorx on 2018-04-27
Today i've installed 18.04 and i'm getting odd problem with it. For some reason after reboot of OS UEFI and grub are enlarged and do not fit into size of screen. To be specific UEFI do not fit, grub still manage to show the most important things in size of screen but clearly is bigger than it supposed to be. On cold boot everything is ok, no oversized uefi nor grub. I wonder how and why OS has any influence on size of uefi and grub.

OS: Ubuntu budgie 18.04 amd64
GPU: Gigabyte Radeon R9 380 4GB
Connection type: display port
Display: Samsung s24e370d.

This is not a big issue to me, i'm more curious about why it happens. Still, if anyone has any idea how to fix it i will definitely give it a try.

---

### Post by oldfred on 2018-04-28
That happened to me, but with nVidia. 
I was then able to right click and get into system settings from display settings. But with18.04 they have moved things around and that may not work.

I do not know AMD, but have you tried nomodeset?
       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

You should not have to do anything.

 [https://ubuntuforums.org/showthread.php?t=2372733](https://ubuntuforums.org/showthread.php?t=2372733)
If your card is supported by AMDGPU, it will be installed when you install Ubuntu. You can only install the AMDGPU-PRO overlay if AMDGPU is installed. If your card is not supported by AMDGPU, the Radeon driver will be installed.
It's automagic now. You don't need to do anything unless you have a need or pressing desire for the overlay-- for instance if you need Vulkan support. In that case, AMD has a script that will take care of it.

---

