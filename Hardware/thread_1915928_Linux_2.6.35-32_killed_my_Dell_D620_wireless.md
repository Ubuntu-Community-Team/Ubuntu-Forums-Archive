---
title: "Linux 2.6.35-32 killed my Dell D620 wireless"
date: 2012-01-27
forum: Hardware
---

### Post by twrock on 2012-01-27
My Dell D620 laptop running Ubuntu 10.10 just finished a software update which included Linux kernel update to 2.6.35-32. Now my Broadcom wireless no longer works. Fortunately I can revert to 2.6.35-31 at boot, but it'd be great if it can be fixed.
(Why is there so much trouble with this chipset?)

---

### Post by madvinegar on 2012-01-27
Please post the result of 

```
lspci
```

---

### Post by twrock on 2012-01-27
Here you go. Thanks.

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 01)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 01)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
03:01.0 CardBus bridge: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller (rev 40)
09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5752 Gigabit Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)

---

### Post by westie457 on 2012-01-27
Hi, Are you using the driver suggested by 'Additional Drivers'? 

If you are try removing then reinstalling them, Have a cable connction set up for the reboot neededbetween the uninstall and reinstall.

My laptop has nearly identical hardware and is running fine after the update using the recommended driver.

---

### Post by madvinegar on 2012-01-27
If what westie suggested does not work, let me know and I will tell you what to do.

---

### Post by madvinegar on 2012-01-27
Or I may as well tell you now just to keep it in mind.

Make sure at synaptics package manager that the following two packages are installed:

```
b43-fwcutter
firmware-b43-installer
```


Then **DE**-activate the STA proprietary driver from "additional drivers".

Reboot and let me know.

---

### Post by twrock on 2012-01-27
Thanks for the help guys. Since both solutions had me disabling the proprietary drivers and rebooting, I went ahead and installed the b43 packages before rebooting. Ended up that that did it. Looks like I don't need the "recommended additional drivers" after all.
Thanks again.

---

### Post by madvinegar on 2012-01-27
> **twrock said:**
> Thanks for the help guys. Since both solutions had me disabling the proprietary drivers and rebooting, I went ahead and installed the b43 packages before rebooting. Ended up that that did it. Looks like I don't need the "recommended additional drivers" after all.
Thanks again.


This is exactly how my laptop works. This is why I insisted on de-activating the STA driver (and _not_ re-installing him afterwords).

Glad I helped!

---

