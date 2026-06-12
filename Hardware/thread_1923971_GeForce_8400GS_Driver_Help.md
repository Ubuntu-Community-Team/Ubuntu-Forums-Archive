---
title: "GeForce 8400GS Driver Help"
date: 2012-02-11
forum: Hardware
---

### Post by BarManager on 2012-02-11
Okokokok, need help before I throw my rig out the freakin' window...

I'm trying to install my 8400GS on 11.10 and when I run the file provided by nVidia, I get the following:

> **NVIDIA Accelerated Graphics Driver for Linux-x86_64 (290.10)]WARNING: You do not appear to have an NVIDIA GPU supported by the 290.10 NVIDIA Linux graphics driver installed in this system. For further details, please see the appendix SUPPORTED NVIDIA GRAPHICS CHIPS in the README available on the Linux driver download page at [www.nvidia.com](www.nvidia.com).[/QUOTE]

[QUOTE=NVIDIA Accelerated Graphics Driver for Linux-x86_64 (290.10)]ERROR: You appear to be running an X server said:**
> www.nvidia.com[/url].


[QUOTE=NVIDIA Accelerated Graphics Driver for Linux-x86_64 (290.10)]ERROR: Installation has failed.  Please see the file '/var/log/nvidia-installer.log' for details.  You may find suggestions on fixing installation problems in the README available on the Linux driver download page at [www.nvidia.com](www.nvidia.com).
[/QUOTE]

When I try and boot it whilst I'm plugged directly into the card, I get a wall of Courier New with a couple of "FAIL"s by some stuff I don't understand. If that's relevant, I'll get the specifics but in the mean time, HELP! :'(

N.B. I'm new to Linux, so as much detail as possible so I can get more familiar with the system. Thanks. :>

---

### Post by oldfred on 2012-02-11
Do not download and install the driver from nVidia. Use the verison provided by Ubuntu.

I had to do this with my Nvidia 9600GT:
To install Ubuntu, boot from the cd press any key at accessibility circle and keyboard, press F6 and then select the nomodeset option.
USB boot - At the menu press tab on the first option to edit the boot options and replaced the 'splash' option with 'nomodeset'. 
then
On first boot after install, press e on getting the GRUB bootloader. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)

Natty or later Video issues. MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

Resetting an out&#8208;of&#8208;range resolution (does not include grub's set gfxmode=640x480)
[https://wiki.ubuntu.com/X/Config/Resolution#Resetting_an_out-of-range_resolution](https://wiki.ubuntu.com/X/Config/Resolution#Resetting_an_out-of-range_resolution)
Repair grub's video mode and other settings
[https://launchpad.net/grub-customizer](https://launchpad.net/grub-customizer)

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

