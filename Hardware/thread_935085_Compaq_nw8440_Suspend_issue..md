---
title: "Compaq nw8440 Suspend issue."
date: 2008-10-01
forum: Hardware
---

### Post by peregrine on 2008-10-01
I have a compaq nw8440 which has a ATI FireGL v5200. I have everything installed but suspend doesn't work. I also have 64bit ubuntu.

I go into suspend mode but it won't come back. The screen is black. The lights are one everything is business as usual, except for the screen not turning on and the hard drive light flashing every few seconds.

---

### Post by peregrine on 2008-10-01
Can someone help me out here? Is the solution to write one of them customer suspend scripts? There must be a fix for this cause suspend used to work on 7.10 32 bit version.

Anyone please?

---

### Post by peregrine on 2008-10-01
Here is my lspci
```
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc M56P [Radeon Mobility X1600]
02:06.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
02:06.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
02:06.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
02:06.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller
02:06.4 Communication controller: Texas Instruments PCIxx12 GemCore based SmartCard controller
08:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5753M Gigabit Ethernet PCI Express (rev 21)
10:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

```

Can anyone assist me?

---

### Post by peregrine on 2008-10-02
Nobody? I don't mean to be annoying I just feel like everyone is ignoring this?

---

### Post by peregrine on 2008-10-03
Can anyone help me?

---

### Post by asg1290 on 2008-11-25
> **peregrine said:**
> Can anyone help me?

Which video driver are you using? Open Source or closed ATI/AMD one?  I have a nw8440 right here running 8.10 using the open source radeon driver and it suspends and resumes all day long with no problems.  Just make sure your accelmethod is EXA when using the open source driver and not the default XAA.  Just put this in your device section in your Xorg.conf

    Option "AccelMethod" "EXA"

Hope that helps

Alex

---

