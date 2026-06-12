---
title: "[SOLVED] Acer Aspire 3680: No Sound After Hibernate"
date: 2007-09-29
forum: Hardware &amp; Laptops
---

### Post by tdrusk on 2007-09-29
I am running an Acer  Aspire 3680. I have sound when I first boot up, but loose it after I hibernate. I have to reboot to fix it. That is really annoying, so...

lspi says: 
```
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller (rev 14)
03:00.0 Ethernet controller: Atheros Communications, Inc. Unknown device 001c (rev 01)
0a:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
0a:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)

```

aplay -l says:
```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

I'm not sure if that will help or not. 

I have seen that a lot of people have fixed this problem with the vanilla kernal 2.6.21 at
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/80893](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/80893)
The links that I followed to the kernal didn't work. They files weren't on the server. So is the vanilla 2.6.20 kernal what I need, or is there a newer version? 

I'm pretty sure when I tested Gutsy it worked better, but not positive.

Well that' s all the information I can give. Any suggestions?

---

### Post by bowmanr@mailcity.com on 2007-10-08
Note : this is not a helpfull response.

I experience exactly the same issue with an IBM R50e laptop and feisty.

Must Shutdown and restart to get sound back. A little frustrating as I want to use the laptop for on the move audio work with ubuntustudio. Oh well, shall wait for a new kernel as it appears that potentially sorts things ...

---

### Post by tdrusk on 2007-10-11
> **bowmanr@mailcity.com said:**
> Note : this is not a helpfull response.

I experience exactly the same issue with an IBM R50e laptop and feisty.

Must Shutdown and restart to get sound back. A little frustrating as I want to use the laptop for on the move audio work with ubuntustudio. Oh well, shall wait for a new kernel as it appears that potentially sorts things ...

Update to Gutsy fixed it.

---

