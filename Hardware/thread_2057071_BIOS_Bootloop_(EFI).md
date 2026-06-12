---
title: "BIOS Bootloop (EFI)"
date: 2012-09-12
forum: Hardware
---

### Post by cre8ive65 on 2012-09-12
When I bought my Acer Travelmate 5560-8225, it had windows 7 on it. I formatted the drive and installed Ubuntu 12.04. Just recently I needed a fresh copy of windows so I formatted the Hard Drive, rebooted, and got windows to start installing. Expanding windows files was stuck at 0% when I quit the installation. Now it tries to boot in the boot order but fails. I hit F2 to get into the BIOS and it beeps and says "Please wait" but instead it reboots. ALT+F10 will give off a beep but won't bring up the recovery. Basically the BIOS posts, but reboots the laptop instead of doing what I tell it. any ideas? :confused:

---

### Post by oldfred on 2012-09-12
Windows only sees NTFS partitions. It knows Linux partitions are used but cannot see them and cannot use them to install. 

If you have UEFI set to boot in UEFI mode it is looking for the efi partition, but if you do not have that it may have issues?

You may want to set drive to gpt partitioning and create the Windows partitions. You can use gparted to create the partitions, but Windows may still want to reformat the NTFS partitions.

Older Windows info on gpt - 2008 updated 2011
[http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx)
Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Windows technical info on gpt and GUIDs
[http://msdn.microsoft.com/library/windows/desktop/aa365449](http://msdn.microsoft.com/library/windows/desktop/aa365449)
Order on drive is important:
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

---

### Post by cre8ive65 on 2012-09-14
So I'm confused, Do I use the drive in another computer to install windows? I believe the laptop is in EFI mode.

---

### Post by oldfred on 2012-09-14
Just erase drive with gparted on Ubuntu liveCD or use gparted liveCD. Then Windows can install in whatever way it decides.

Both Windows & Ubuntu will boot in either UEFI mode or BIOS mode and whichever way booted will be the way they install.

---

