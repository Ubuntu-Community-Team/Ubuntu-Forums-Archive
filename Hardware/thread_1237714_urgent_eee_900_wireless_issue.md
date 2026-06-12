---
title: "urgent eee 900 wireless issue"
date: 2009-08-11
forum: Hardware
---

### Post by djzoid on 2009-08-11
this damn laptop only gives me strife and hours of fun if im using linux! my wireless is screwed, i would like to know how i would go about finding out if the problem is the laptop or my jaunty install? i just started it and the only reason im writing this message is cos im using a wireless usb card so i would gues its a hardware fault which is a real boner, but as with anything linux orientated, it could be bloody any number of software problems, i suspect. 
so if any1 could give this poor newb some advice he might be able to send u a smilie. theyre worth a lot these days, i hear.:P

---

### Post by sergiom99 on 2009-08-11
post the output of lspci (typed in a Terminal) to find out which wifi card do you have. You never mentioned it.

Any additional details besides of "screwed" might be of more help also.

---

### Post by djzoid on 2009-08-17
sorry i should have said, when i turn my eee on, it does not register any networks under the wireless network connections icon. so it is as if the wireless is turned off although the wireless box is checked and the blue light is on and is turned on in the bios.

here is the readout when i execute the lspci command:

00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 04)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 04)
00:1c.2 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
01:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
03:00.0 Ethernet controller: Attansic Technology Corp. L2 100 Mbit Ethernet Adapter (rev a0)

---

### Post by vinnywright on 2009-08-17
your wirless card is being detectid by the sys.

> 01:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)you could do 

```
iwconfig
```to see if the sys. is acualey trying to use it...........and

```
lsmod
```to see if the modual for it is being loaded..........I think it should be eather ath_pci, ath5k or ath9k

mine is the AR5008 chipset and allthough the ath9k tryed to work it I never got mutch out of it untill I used ndiswrapper to load the XP driver

VINNY

---

### Post by djzoid on 2009-08-20
thank you for the advice, it was using the madwifi driver cos i changed it at some point when following instruction to install warcraft or something. stupid me. im happily browsing the web using the atheros driver like im supposed to be! it was confusing me because there was nothing actually wrong other than the madwifi driver didn't seem to work or maybe it was not configured properly. is it actually better in any way than the ath5k driver?

---

