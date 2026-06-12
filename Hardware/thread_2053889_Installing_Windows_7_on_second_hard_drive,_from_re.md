---
title: "Installing Windows 7 on second hard drive, from recovery partition"
date: 2012-09-06
forum: Hardware
---

### Post by charliemarquez on 2012-09-06
Hello,

My Lenovo T420 came with a standard HD and Windows 7 installed on it. I just finished the first boot setup and changed it with a SSD where I've installed Ubuntu.
Now I need to dual boot. So I bought a DVDcase adaptor for the old HD in order to use Window as a plug-in OS.
Unfortunately I could not boot from that disk. Can I reinstall Windows on the second hard drive from the recovery partition?

---

### Post by black veils on 2012-09-06
your problem is likely to be bios or boot-loader configuration, there wont be any point to reinstalling operating systems.

maybe you could try: [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by oldfred on 2012-09-06
Recovery partitions are just images of the hard drive, not full installers. All they really do is copy the image of the drive as purchased back to the hard drive?

Windows only boots from internal drives. Is your adaptor configure drive as internal or is it more like a USB external? 

The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2040149](http://ubuntuforums.org/showthread.php?t=2040149)
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

Make your own Windows repairCD (not vendor recovery):
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

