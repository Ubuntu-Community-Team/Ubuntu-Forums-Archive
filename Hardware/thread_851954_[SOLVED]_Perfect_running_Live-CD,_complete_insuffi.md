---
title: "[SOLVED] Perfect running Live-CD, complete insufficient hardwaredetection after HDins"
date: 2008-07-07
forum: Hardware
---

### Post by rodoc on 2008-07-07
Hello friendly community:)
My Laptop: Dell Latitude D505 1400x1050 (XGA+) Intel 855GM/GME videocontroller, 1GB Ram

Live CD with 8.04 and 8.04.1 runs perfect.
correct (intel=i810) viodeomode with 3D support and compiz desktop effekts
mounting of partitions (1x NTFS, 2x ext3), not mounting 1x SunOS but bootable via grub which is ok (Installed OS: 1x XP, 1x Suse 10.1, 1x Sun Solaris)
running sound system
running ethernetcontroller
running wireless lan (after installation via internet) broadcom bc43xx
icons on the desktop
running usb mouse, touchpad
mounted cd drive
mounting usb devices

installation from live cd (running or from bootmenu) or alternate cd, with acpi or acpi=0, noacpi, nalacpi or none of them (both 8.04, 8.04.1) ends all in the same result:

vesa videomode (change after first boot to i810 and 1400x1050 has no effect) with 1280x1024 and disabled 3D, down shifted screen (about 50 pixels, screen starting with pixel 1 at about position 900, when line is full filling the rest from postion 1 to 899 = somewhat splitscreen)
touchpad running

not detected:
ethernetcontroller, wireless Lan controller, usb mouse, cd drive, usb devices, no icons on desktop, no sound, mountable only the own ext3 partition, none of the others

repeated errormessages from the bootscreen: (what i could manage to read) Could not load /lib/modules/2.6.16.21-0.25-smp/modules.dep
I found the same errormassages in the sys.log
on HD there is only /lib/modules/2.6.24-19-generic !!!

I'm booting from grub (created and modified in Suse 10.1). Did not install grub from ubuntu, am anxious of MBR problems. Each of the four OS's starts fine. I think this should not be the cause of my problem

Working on the problem for more than 2 weeks, read a lot of FAQ's and help-forums and could not find a solution

Thanks a lot for help (Linux semi-newbie)

---

### Post by rodoc on 2008-07-08
Finally i myself found the cause of the problem. Grub (from Suse 10.1) started after autoconfiguration with the kernel from Suse into Ubuntu. I didn't check this because in grub only the path image=/boot/vmlinuz was defined and not the full kernelfilename. The kernel.log showed me the way to the error because it could not load desired drivers from kernel 2.6.16.21-0.25-smp which is definitely not the accurate kernel for Ubuntu 8.04.1. For me its absolutely amazing that a Suse Kernel can start a system behaving and looking like Ubuntu.

A problem seldom appears alone, my bios could not start ubuntu from the partition where it has been installed (fourth partition on the very end of the HD with 250 GB). This resulted in error 18 from grub.

Solution: deletion of SUSE 10.1, installation of Ubuntu in this position, slight modification of the Ubuntus grub menu and success !!!! (for starting a solaris partition you have to set the boot and active flag with gparted)

---

