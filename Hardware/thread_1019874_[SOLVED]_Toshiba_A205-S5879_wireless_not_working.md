---
title: "[SOLVED] Toshiba A205-S5879 wireless not working"
date: 2008-12-23
forum: Hardware
---

### Post by chudder on 2008-12-23
Hi Everyone,

I searched the forums and there are posts similar to this one and I tried what was suggested in the forums but to no avail.  Someone suggested I start my own thread so that's what I'm doing.  

I just got a toshiba satellite A205-S5879 and I like it but it's not reading the wireless hardware which is supposedly by Atheros, I don't know what kind but it has the driver pre-installed when I installed Intrepid.  A lot of the the hardware including brightness adjustment with a Phoenix BIOS works well so I'm impressed with that.  

How should I go about fixing this problem?

Thank you to all who help very much!

Chud

---

### Post by chudder on 2008-12-23
I just realized another problem, the default Atheros driver can't be activated.  I don't know why.  It was activated before but then I deactivated it because I trying some of the solutions for this problem on the forums but now it won't deactivate.  What should I do here?

---

### Post by stchman on 2008-12-23
Please give us an lscpi output in this thread.

If you are using Intrepid try this:

```
sudo apt-get install linux-backports-modules-intrepid-generic
```

These kernel modules have better support for newer Atheros cards.

---

### Post by chudder on 2008-12-23
```

sudo lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)
05:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
0c:04.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
0c:04.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
0c:04.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
0c:04.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller

```

---

### Post by chudder on 2008-12-23
> **stchman said:**
> Please give us an lscpi output in this thread.

If you are using Intrepid try this:

```
sudo apt-get install linux-backports-modules-intrepid-generic
```

These kernel modules have better support for newer Atheros cards.

This is the output, is there a typo in the code?

```
sudo apt-get install linux-backports-modules-intrepid-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-backports-modules-intrepid-generic
 
```

---

### Post by chudder on 2008-12-24
> **stchman said:**
> Please give us an lscpi output in this thread.

If you are using Intrepid try this:

```
sudo apt-get install linux-backports-modules-intrepid-generic
```

These kernel modules have better support for newer Atheros cards.

Thanx!  This worked at least for now and hopefully forever!  Thank you very much!

---

### Post by stchman on 2008-12-29
> **chudder said:**
> Thanx!  This worked at least for now and hopefully forever!  Thank you very much!

Remember to put

ath5k

in your /etc/modules

This will ensure that the kernel module is loaded everytime you boot.

---

