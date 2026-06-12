---
title: "Installation issue on VMWare"
date: 2009-01-20
forum: Installation &amp; Upgrades
---

### Post by sudheerah on 2009-01-20
I installed VMWare server 1.0.4 in my laptop (Vista Home Basic) and try to install Ubuntu desktop 8.04 on VMWare. I mapped the ubuntu installation file to the CD-ROM of the VMWare. But halfway through in the installation wizard, there was a one step stating that "allocation of disk space". But there, it won't show anything to do the allocation.
Although in the VMWare installation I allocated 15 GB for the server.

Can anybody figure out the issue.


Thanx in Advance.

---

### Post by OldManRiver on 2009-03-05
> **sudheerah said:**
> I installed VMWare server 1.0.4 in my laptop (Vista Home Basic) and try to install Ubuntu desktop 8.04 on VMWare. I mapped the ubuntu installation file to the CD-ROM of the VMWare. But halfway through in the installation wizard, there was a one step stating that "allocation of disk space". But there, it won't show anything to do the allocation.
Although in the VMWare installation I allocated 15 GB for the server.

Can anybody figure out the issue.


Thanx in Advance.
Sorry but have to insert my opinion, reason for running VMWare is not to let you run Linux underneath a troubled and faulty system but the opposite, run the Vista under a stable and robust Linux system.

If you have Vista, then assumption is this is realatively new system, so you need to:

1. Scour internet for right Linux hardware drivers for your machine and download. Burn all onto seperate CD,
2. Download/Burn Ubuntu Live CD.  Suggest 7.10 as some systems have problems with installs on 8.04,
3. Download Rescue Disk and install, make iso of all your current system and/or critical data.
4. Load Ubuntu with full disk format (Yes hard format of 100% of drive),
5. Install your hardware drivers, if not in native install,
6. Install VMWare then Vista (this can be problematic so be careful),
7. Restore Windows data,
8. Upgrade Ubuntu to 8.04.

Not an easy process and if you only have one machine, you can choke in the middle, so do it in planned and careful mode, to avoid as many problems as possible.

I say careful, cause I'm in the middle of this process and having VMWare issues of my own, but have multiple machines, so I moved all data off machine via network first and restoring that way.

OMR

---

