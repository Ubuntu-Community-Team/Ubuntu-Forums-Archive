---
title: "Adding drivers to ISO for Live CD before buring"
date: 2012-09-20
forum: Hardware
---

### Post by ominub on 2012-09-20
Hello all

I am a Digital Forensics student and I use Linux live cds almost daily. I typically install the distros to flash drives for speed reasons so this may be possible after installation, but who knows.

I am using an HP laptop for my forensic examinations. When I boot the live cds/Flash Drives my resolution is crap; 800x600 usually, sometimes lower. I am curious, is it possible to add the driver software for my, or any, video card to the ISO so that it will run when I boot the live cd?

If it is possible, where would the driver need to be located? All the forensic live cds I use are based on some version of Ubuntu. Helix is the one I use the most, it's built on Ubuntu 8.04. I also use Raptor, SIFT, and Backtrack a few times a month because some distros include tools that the others do not. 

I'm pretty sure the install script(s) would need to be updated as well to include the additional drivers. I can figure out how to do this if someone could let me know where to find the scripts.

Thanks in advance for the help. I will keep digging through these ISOs to see if I can find anything, and I'll post updates if I figure anything out.

---

### Post by ominub on 2012-10-03
bump...

---

### Post by oldfred on 2012-10-03
I am pretty sure there are ways to do what you want. Do not think they would then fit on CD, but on USB flash drive that should work.

Have you tried a persistent install or  a full install to the flash drive?

Pros & cons of persistent install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

With grub2 persistent C.S.Cameron 12.04
[http://ubuntuforums.org/showthread.php?t=2042965](http://ubuntuforums.org/showthread.php?t=2042965)

Full install of 12.04 to USB device C.S.Cameron post #5
[http://ubuntuforums.org/showthread.php?t=2060493](http://ubuntuforums.org/showthread.php?t=2060493)

With grub2's loopmount you can also have many ISO booted with grub2 on one flash device. I think only one can be persistant.

These are scripts to install many ISOs. Some that will not loopmount by installing a kernel and boot image.
MultiBootUSB - Install and boot multiple Linux from Pendrive / Flash drive / USB disk w/grub2
[https://help.ubuntu.com/community/InstallAndBootMultipleLinuxFromPendriveFlashDriveUSBDisk](https://help.ubuntu.com/community/InstallAndBootMultipleLinuxFromPendriveFlashDriveUSBDisk)
[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)
[http://sourceforge.net/projects/multibootusb/files/](http://sourceforge.net/projects/multibootusb/files/)
MultiSystem Another LiveUSB Multiboot French(translate) w/grub2 
[http://liveusb.info/dotclear/](http://liveusb.info/dotclear/)
Another: multiboot055.sh
[http://blog.p-mt.net/blog/2009/12/27/multiboot-usb-stick/](http://blog.p-mt.net/blog/2009/12/27/multiboot-usb-stick/)

It does not have to be encrypted BIOS based system:
Standard full install with screenshots to flash or SSD:
Ubuntu Encrypted Flash Memory Installation using alternative text based installer
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)

---

