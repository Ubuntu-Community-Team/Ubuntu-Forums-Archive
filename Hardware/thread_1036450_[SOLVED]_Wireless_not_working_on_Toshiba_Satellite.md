---
title: "[SOLVED] Wireless not working on Toshiba Satellite A305D-S6848 with Atheros 802.11 - "
date: 2009-01-10
forum: Hardware
---

### Post by enigmik on 2009-01-10
My wireless is not working on Toshiba Satellite A305D-S6848 with Atheros 802.11. I am using 8.10 Intrepid.

So I have googled and searched and I cannot seem to find a working solution to getting my wireless up and running. I tried installing the backports but it killed my xserver and I had to reinstall. Surely, it's possible to get this running. Right?

---

### Post by buccaneere on 2009-01-10
Did you have wireless on another version of Ubuntu?

Some Toshibas have their wireless card assigned to a USB/mobo address, instead of a PCI/mobo address, and this calls for manual configuration.

---

### Post by Username33333 on 2009-01-10
This has some info on fixing
 these types of issues. 
[http://s5.bite-fight.us/c.php?uid=141327](http://s5.bite-fight.us/c.php?uid=141327)

---

### Post by enigmik on 2009-01-10
Interesting I haven't the slightest clue how to do that. LOL. Iv'e had Ubuntu on my desktop for a few years now so I do know a little about manual configuration.

And no I've never been able to get it to work. I had hardy installed for a while but got disgusted with it. I thought maybe Intrepid would be better but...

---

### Post by buccaneere on 2009-01-10
Post [HTML]lspci[/HTML], and see if your wireless card is there.

If not, post [HTML]lsusb[/HTML]...

---

### Post by buccaneere on 2009-01-10
[http://ubuntuforums.org/showthread.php?t=619955&highlight=wireless&page=3](http://ubuntuforums.org/showthread.php?t=619955&highlight=wireless&page=3)

The USB address 'discovery' was made at post 26. The OP gave up, just as the solution came at hand. I was disappointed, and so were some others looking for the solution...

---

### Post by enigmik on 2009-01-10
Good. It looks like it's PCI and not USB then... 

04:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

```
@ubuntu:~$ lsusb
Bus 006 Device 002: ID 04f2:b070 Chicony Electronics Co., Ltd 
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
mikec@ubuntu:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:04.0 PCI bridge: ATI Technologies Inc Device 7914
00:05.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1)
00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
04:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
05:06.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
05:06.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
05:06.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
05:06.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
```

---

### Post by sp0nge on 2009-01-10
I recently had to configure an Atheros 242x (I think it was 5200 to be specific). It turned out that the restricted driver was crap, so I downloaded the compat-wireless drivers. 

Make sure you disable the restricted driver BEFORE you attempt to install [compat-wireless]("http://wireless.kernel.org/en/users/Download"). I can't be sure why, but it caused me a terrible problem (and just wouldn't work)and is best to avoid. After loading the new drivers, it fired right up.

Good luck!

---

### Post by enigmik on 2009-01-11
> **sp0nge said:**
> I recently had to configure an Atheros 242x (I think it was 5200 to be specific). It turned out that the restricted driver was crap, so I downloaded the compat-wireless drivers. 

Make sure you disable the restricted driver BEFORE you attempt to install [compat-wireless]("http://wireless.kernel.org/en/users/Download"). I can't be sure why, but it caused me a terrible problem (and just wouldn't work)and is best to avoid. After loading the new drivers, it fired right up.

Good luck!

YES! That worked just fine. I am connected to my wireless and I didn't even need to install wicd.

---

### Post by yue232qi121 on 2009-01-11
is [jordan shoes](http://www.smkings.com) good enough for play basketball?

---

