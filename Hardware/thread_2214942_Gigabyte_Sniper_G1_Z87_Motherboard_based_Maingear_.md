---
title: "Gigabyte Sniper G1 Z87 Motherboard based Maingear Shift system -no Linux Live CD Boot"
date: 2014-04-03
forum: Hardware
---

### Post by macsociety on 2014-04-03
Just purchased a new Maingear Shift system.... tried many Linux Live DVDs and non seem to work.

Wanted to erase drive of Windows 8.1 (blah) and go Linux only, specifically Ubuntu Gnome 13.10

I turned off Secure Boot in Bios on system but other than getting old Debian based GPARTED Live DVD to boot, and Debian 7.04 in Safe Mode, I have issues with better distros like Ubuntu.

The system has a Gigabyte G1 Sniper Z87 Motherboard with i7 4770 processor, 16GB Corsair Vengence RAM, 1GB HDD, and I can boot the Live GNOME 13.10 DVD but.... when I click on Run so I can see what it looks like, all these scrolling IP addresses fill the screen and that is it... she is locked up in an endless loop of these IP addresses.

I am afraid to select the Install option because if the Live DVD does not work, then I don't want to screw up my Windows install since it does work.

Funny think is I installed Virtualbox and then installed Ubuntu Gnome 13.10 on it, and she runs fine.

So, must be just some setting I don't have right in Bios or.... maybe this board is just not compatible.

I am no linux expert but would love to run it as my main OS and get rid of Windows.

Any help would be great!

TJ

---

### Post by oldfred on 2014-04-04
This is mostly older model Gigabyte boards, not sure if any still applies.
 Gigabytes P67 & H67 hybrid efi -Hybrid EFI is a UEFI based on the open source TianoCore
[http://www](http://www).[rod]("http://www.rodsbooks.com/gb-hybrid-efi/")sbooks.com/gb-hybrid-efi/
[http://gigabytedaily.blogspot.com/2011/01/gigabyte-hybrid-efi-technology.html](http://gigabytedaily.blogspot.com/2011/01/gigabyte-hybrid-efi-technology.html)
Gigabyte GA-X79-UD3 with I7-3820
Needed F6 to set ACPI=Off.and nomodeset
Gigabyte UEFI boot issues - The partition size of the created USB Installer device needs to be under that of 4GB. 
Others found UEFI/BIOS update solved issue of 4GB FAT limit.
turns out the IOMMU needs to be enabled in the BIOS. This problems seems to be exclusive to Gigabyte boards.

Some with new 4th Gen Haswell Intel chips have needed 14.04. Intel made many improvements to kernel, support software and video drivers and those are mostly in 14.04. 

What video processor, internal Intel or did you add a video card?
Are you booting in UEFI or BIOS boot mode. How you boot installer is how it installs.

      
 Haswell improvements thru 2013
[http://www.phoronix.com/scan.php?page=article&item=intel_2013haswell_end&num=1](http://www.phoronix.com/scan.php?page=article&item=intel_2013haswell_end&num=1)
Intel Haswell - Linux support June 2013
[http://www.phoronix.com/scan.php?page=news_item&px=MTM5MzU](http://www.phoronix.com/scan.php?page=news_item&px=MTM5MzU)

You may just need a boot parameter or two. 
      
 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

---

