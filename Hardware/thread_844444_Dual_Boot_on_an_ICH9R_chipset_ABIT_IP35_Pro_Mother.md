---
title: "Dual Boot on an ICH9R chipset ABIT IP35 Pro Motherboard"
date: 2008-06-29
forum: Hardware
---

### Post by knownrider on 2008-06-29
Installing Windows XP and Ubuntu onan ABIT IP35 Pro motherboard with the ICH9R chipset...  For other people who may need the info, here are the steps I took.


1. Download the latest ICH9R drivers.  At the Intel download site, search for ICH9R chipset drivers, and download the latest "Intel Matrix Storage Manager" drivers for Windows XP.  There should be one specifically labeled the "F6" version.  Copy this directly to a fresh floppy disc and label it.

2. Boot into the Bios setup menu, and set the the chipset sata controllers to RAID.  In my Bios this was done by: Integrated peripherals> OnChip SATA Device> RAID.

3. Set The Bios to boot your CD/DVD-ROM device first and insert the Windows XP disc.

4. Reboot into the Windows install blue screen and hit F6 to "Install third-party drivers".

5. When prompted insert the floppy with the Intel Matrix storage drivers.  Select the one that handles "ICH9R RAID".

6. Follow the on-screen instructions to complete the Windows XP install.  For best results, partition your boot drive into two sections: one for Windows and one for Linux.

7. When the Windows install is complete, reboot with the install disc for Linux.  Linux won't need to add any additional drivers during install.

8. Install Linux to the unused boot drive partition.  Linux will install the GRUB boot loader, which will recognize and allow you to boot both Linux and Windows.  I recommend having Linux "mount" your boot drive partition at "/", and mount another drive at "/home".  This way you can change your entire system without losing your settings or files.  If you do it this way you don't need very much disk space for Linux's system.  I use about 12GB's for Linux, and 2-3GB for swap space.   This is more than you need but disk space is cheap.

---

### Post by ubumac on 2008-08-02
Quick question, does the raid config work for XP and Linux? I have that same on-board chip. Since raid config requires the F6 driver load during XP installation, it made me wonder if the raid config would only be recognized by windows. Any information is appreciated.

Thanks,

John

---

