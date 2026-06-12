---
title: "issues installing ubuntu for dual-boot on new laptop"
date: 2018-06-04
forum: Hardware
---

### Post by b3po on 2018-06-04
I just recently purchased an MSI Stealth-Pro GS63VR laptop and it came pre-installed with Windows 10 :mad:, the latest edition. These are the specs:

[TABLE]
[TR]
[TD]**MSI Stealth Pro GS63VR**[/TD]
[/TR]
[TR]
[TD]**Screen**[/TD]
[TD]15.6 inch, 1920 x 1080 resolution, IPS, 60 Hz, Wide angle[/TD]
[/TR]
[TR]
[TD]**Processor**[/TD]
[TD]Intel Skylake Core i7-6700HQ CPU, quad-core 2.6 GHz(3.5Ghz boost)[/TD]
[/TR]
[TR]
[TD]**Video**[/TD]
[TD]Intel HD 530 and NVIDIA GTX 1060 with 6GB GDDR5 VRAM[/TD]
[/TR]
[TR]
[TD]**Memory**[/TD]
[TD]16 GB DDR4 2400Mhz (2 x DIMMs)[/TD]
[/TR]
[TR]
[TD]**Storage**[/TD]
[TD]128 GB M.2 SATA + 1 TB 5200rpm HDD
[/TD]
[/TR]
[TR]
[TD]**Connectivity**[/TD]
[TD]Killer Wireless-AC 1535, Qualcomm Atheros Bluetooth 4.1(Intel for the -001 model)[/TD]
[/TR]
[TR]
[TD]**Ports**[/TD]
[TD]3x USB 3.0, Thunderbolt 3, HDMI 1.4b, mini-DP, USB 2.0, mic, earphone, ethernet[/TD]
[/TR]
[TR]
[TD]**Battery**[/TD]
[TD]57 Wh[/TD]
[/TR]
[TR]
[TD]**Operating system**[/TD]
[TD]Windows 10[/TD]
[/TR]
[TR]
[TD]**Size**[/TD]
[TD]380 mm or 14.96&#8221; (w) x 249 mm or 9.80&#8221; (d) x 17.7 mm or .70&#8221; (h)[/TD]
[/TR]
[TR]
[TD]**Weight**[/TD]
[TD]1.8 kg or 3.96 lb[/TD]
[/TR]
[TR]
[TD]**Extras**[/TD]
[TD]Multi-colored backlit keyboard, trackpad, HD webcam[/TD]
[/TR]
[/TABLE]

I have only used macOS and a few Linux distros for the past several years and after only a few days using this new Windows I can't stand it. I have unallocated 500GB of the HDD in order to install Ubuntu for my everyday use (in school for CS), and leave everything else as is for now for gaming purposes. I burned a .iso for the most recent version (18.04) to a flash drive, but when I boot to it no matter if I select install Ubuntu or try before installing the screen freezes as soon as the GUI loads. I am fairly sure this has something to do with the graphics card and possibly other compatibility issues. I followed advice in this [thread]("http://ubuntuforums.org/showthread.php?t=2353061"), but had no luck thus far. I just tried disabling the GTX 1060 from within Windows, then rebooting into the flash drive; I had GUI functionality for all of about 5 seconds before it froze again. Does anyone have an idea as to what else I could try?

---

### Post by b3po on 2018-06-09
Bump. I really want to get back to using Linux, any suggestions will be greatly appreciated.

---

### Post by oldfred on 2018-06-09
Have you updated UEFI.
Many with M.2 SATA drives also needed firmware update to drive.

Are drives in UEFI settings, set for AHCI, not RAID, not IDE nor Intel SRT? (Unless really RAID 0).
 If not change, but add AHCI driver in Windows first.

Is Windows fast start up off. That is just hibernation.

With nVidia you will need nomodeset boot parameter.
       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

See also link in my signature below.

Other MSI, often issues common across many models of same brand.
       MSi GT72VR-6RE Dominator Pro - some settings required
[https://ubuntuforums.org/showthread.php?t=2365997](https://ubuntuforums.org/showthread.php?t=2365997)
Failing to Boot Ubuntu 16.10 in MSI GP72
[http://askubuntu.com/questions/838212/failing-to-boot-ubuntu-16-10-in-msi-gp72](http://askubuntu.com/questions/838212/failing-to-boot-ubuntu-16-10-in-msi-gp72)
[SOLVED] MSI GT72S 6QE - Freezes on boot unless acpi=off is used
[http://ubuntuforums.org/showthread.php?t=2303544](http://ubuntuforums.org/showthread.php?t=2303544)
MSI GS60 2QE 2xSSD RAID 0 + 1TB HDD dual boot w8.1/w10 problem 
[http://ubuntuforums.org/showthread.php?t=2297815](http://ubuntuforums.org/showthread.php?t=2297815) [URL="http://ubuntuforums.org/showthread.php?t=1613132"]
[/URL]

---

