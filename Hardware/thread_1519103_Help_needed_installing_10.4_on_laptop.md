---
title: "Help needed installing 10.4 on laptop"
date: 2010-06-27
forum: Hardware
---

### Post by walkerx on 2010-06-27
Hi all,

I'm currently running 9.10 on my laptop and downloaded 10.4 to install.

I've tried both netbook edition and desktop edition but neither will install. The Ubuntu loading screen shows then the dots all go red after a while, then the screen goes blank.

On previous versions u could change some of the options on bootup, but i've not seen these on 10.4.

Anyone any ideas or should i just stick with 9.10

thanks

lspci shows the following:

00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
02:04.0 CardBus bridge: Texas Instruments PCI1520 PC card Cardbus Controller (rev 01)
02:04.1 CardBus bridge: Texas Instruments PCI1520 PC card Cardbus Controller (rev 01)
02:0a.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
03:00.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

---

### Post by mikewhatever on 2010-06-27
In case you know you need to change boot options, hit any key after the BIOS screen, as soon as the purple background appears.
The problem is likely your graphics.
```
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
```
See Lucid release notes for more info.
[https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Intel%208xx%20X%20freezes/crashes](https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Intel%208xx%20X%20freezes/crashes)

---

### Post by walkerx on 2010-06-27
> **mikewhatever said:**
> In case you know you need to change boot options, hit any key after the BIOS screen, as soon as the purple background appears.
The problem is likely your graphics.
```
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
```
See Lucid release notes for more info.
[https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Intel%208xx%20X%20freezes/crashes](https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Intel%208xx%20X%20freezes/crashes)

thanks will give this a try an report back

that worked a treat: now to get my broadcom bcm4306 working again

---

