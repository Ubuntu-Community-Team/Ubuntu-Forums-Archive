---
title: "&quot;Create a USB Startup Disk&quot; works but I have partitioning problems with the installer"
date: 2008-11-22
forum: General Help
---

### Post by altonbr on 2008-11-22
To be more specific, I am using the ubuntu-8.10-alternate-i386.iso ISO and a generic 2GB flash drive.

"Create a USB Startup Disk" works quite well and it told me to reboot.

I hit F12 and was able to boot to my USB stick, and run the alternate installer.

This is where the problem begins: the installer can not find the USB stick for partitioning, so when it is trying to install Ubuntu, it can't find itself and install it to the USB flash drive.

I see my SATA3 (/dev/sda) and SATA4 (/dev/sdb) hard drives - 250GB WD and 500GB Seagate respectively - but not the Flash drive.

How am I to install Ubuntu to the Flash drive when it can not read it during the installer?

---

### Post by jamieh on 2008-11-22
That is an odd problem. Have you tried any other flash drives?

---

### Post by altonbr on 2008-11-22
> **jamieh said:**
> That is an odd problem. Have you tried any other flash drives?

No I haven't, but I'll try my 2GB Cruzer Micro now.

Am I supposed to use a different CD image other than 'alternate'?

And how is this supposed to work anyway? The USB disk has the installation files on it and then it's supposed to be partitioned for Ubuntu to install to. That just doesn't make any sense.

Shouldn't it be that you install a USB flash drive from a alternate CD, instead of putting the alternate CD files on the flash drive, which you're about to install to.

Do you see my confusion?

The installation files will be wiped out by the installation had I actually gone through with it.

EDIT:: this was my 1200th post, woot!

---

### Post by aymhenry on 2008-11-23
Pleae see us the result of this command, it may help

sudo fdisk -l

---

