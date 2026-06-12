---
title: "Install of Epson XP-200 Printer/Scanner"
date: 2016-04-11
forum: Hardware
---

### Post by windowsfree on 2016-04-11
Hello,

I am using Ubuntu Gnome 14.04 and when attempting to install the detected XP-200 printer connected via USB, the driver install never finishes.  I let it go for about 45 minutes and it never installed.  I downloaded the driver (DEB) for it and the same occurs after downloading the printer.  I restarted the OS between the OS detection and installed the DEB file.   No printer installed.  I restarted the OS again and still no printer installed.   Any suggestions?

Thank you.

---

### Post by wabbit46 on 2016-05-05
> **windowsfree said:**
> Hello,

I am using Ubuntu Gnome 14.04 and when attempting to install the detected XP-200 printer connected via USB, the driver install never finishes.  I let it go for about 45 minutes and it never installed.  I downloaded the driver (DEB) for it and the same occurs after downloading the printer.  I restarted the OS between the OS detection and installed the DEB file.   No printer installed.  I restarted the OS again and still no printer installed.   Any suggestions?

Thank you.

I had the same problem. However I discovered that the printer appeared in the list of available Epson printers after the driver install was attempted. Picking it from the list installed it. Hope this helps.

---

### Post by Mark Phelps on 2016-05-05
I had similar problems using the epson-inkjet-printer-201112w_1.0.0-1lsb3.2_amd64.deb in Mint 17.2 and discovered that the Epson installer expects the package "lsb" to be already installed and if it is not, the installer just hangs -- which sounds like what is happening to you.

I recently installed Ubuntu 16.04 and found that the packages that were already installed were lsb-base and lsb-release, so you might need these, instead.

Good Luck

---

### Post by Linuxisfast on 2016-05-09
lsb and lsb-release have been removed from Debian/Ubuntu Xenial base unfortunately.

---

