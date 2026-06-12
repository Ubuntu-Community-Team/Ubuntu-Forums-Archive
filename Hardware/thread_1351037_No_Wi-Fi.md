---
title: "No Wi-Fi"
date: 2009-12-10
forum: Hardware
---

### Post by ..::| Dave89 |::.. on 2009-12-10
I installed Ubuntu 9.10 on my Acer 5315 laptop, no Windows, just Ubuntu, so far everything works fine, except for the in-built Wi-Fi, the Wi-Fi indicator lamp isn't lit, and t won't pick up any networks. I've temporarily fixed the problem by using a USB Wi-Fi key, but would still like the internal Wi-Fi to work. Perhaps some drivers or something would help?

TIA

---

### Post by Greenwidth on 2009-12-10
Post the output of:
```
lspci
```

to determine your wireless chipset

---

### Post by ..::| Dave89 |::.. on 2009-12-10
dave89@dave89-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
05:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
06:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
dave89@dave89-laptop:~$

---

### Post by Bucky Ball on 2009-12-10
Plug in an ethernet cable and get all updates. It should pick up if you need a driver for your wireless. Then:

System->Administration->Hardware Drivers.

Is there a wireless driver in there disabled?

Your Broadcom Corporation BCM4312 802.11b/g (rev 01) should work after this procedure. They normally work 'out of the box' after updating via an ethernet cable.

---

### Post by Greenwidth on 2009-12-10
If for some reason you can't get on the net, the driver is on the CD in:
/pool/restricted/b/bcmwlbcmwl-kernel-source_5.10.91.9+bdcom-0ubuntu4_i386.deb

---

### Post by ..::| Dave89 |::.. on 2009-12-10
I have no ethernet access where I am, only Wi-Fi.  How do I install the driver from the install CD?  I double clicked on the .deb, and got the message: "Error: Dependency is not satisfiable: dkms"

---

### Post by Greenwidth on 2009-12-10
Sorry , looks like I was wrong - "Ubuntu 9.04 (Jaunty Jackalope) and Ubuntu 9.10 (Karmic Koala) do provide the b43 drivers, but due to copyright reasons not the proprietary firmware which is required to run your card."

See: (+install instructions)
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

Seems strange though, I have the same card but did not have to do any of this. 
I have dkms installed (the same version thats on the cd - /pool/main/d/dkms) & the driver thats on the cd, but not fw-cutter as mentioned in the wiki, nor did I update the firmware.

---

### Post by ..::| Dave89 |::.. on 2009-12-10
I'm still not 100% on what I have to do :-(

---

### Post by Bucky Ball on 2009-12-10
> **Greenwidth said:**
> Sorry , looks like I was wrong - "Ubuntu 9.04 (Jaunty Jackalope) and Ubuntu 9.10 (Karmic Koala) do provide the b43 drivers, but due to copyright reasons not the proprietary firmware which is required to run your card."



The B43 driver will call up the firmware (b43-fwcutter) and you need to respond in the affirmative to install it. Simple as that. Can't be included for legal reasons. You have to personally agree to terms of use therefore it can not be included in Ubuntu install (like a lot of other things).

---

### Post by Greenwidth on 2009-12-10
Ah Ok.

As its all on the CD, try:
In System > Admin > Software Sources check the installable CD box at the bottom

Then look in System > Admin > Hardware Drivers

---

### Post by Bucky Ball on 2009-12-10
Failing that, once you have assigned the install cd as a software source as described above, go to Synaptic Package Manager and search for b43.

---

### Post by ..::| Dave89 |::.. on 2009-12-10
It's all up and running, thanks for all your help! I did it Greenwidth's way.

---

### Post by Whisp3r on 2009-12-11
I have done the same thing and it worked. Thank you very much.

---

