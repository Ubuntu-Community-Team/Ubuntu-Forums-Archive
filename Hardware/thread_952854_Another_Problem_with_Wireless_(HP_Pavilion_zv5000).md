---
title: "Another Problem with Wireless (HP Pavilion zv5000)"
date: 2008-10-19
forum: Hardware
---

### Post by sexynjig on 2008-10-19
After a fresh install of Ubuntu the PCMCIA cards are not working and the wireless is not working.  I have spent several hours researching and trying new things.  This site claims that the wireless doesn't work out of the box but it does after using ndisrapper.  I tried ndiswrapper and I still can't get it to work.  I guess the problem is that it supposedly uses a BroadCom card but after "lspci" I get the following:

00:00.0 Host bridge: nVidia Corporation nForce3 Host Bridge (rev a4)
00:01.0 ISA bridge: nVidia Corporation nForce3 LPC Bridge (rev a6)
00:01.1 SMBus: nVidia Corporation nForce3 SMBus (rev a4)
00:02.0 USB Controller: nVidia Corporation nForce3 USB 1.1 (rev a5)
00:02.1 USB Controller: nVidia Corporation nForce3 USB 1.1 (rev a5)
00:02.2 USB Controller: nVidia Corporation nForce3 USB 2.0 (rev a2)
00:06.0 Multimedia audio controller: nVidia Corporation nForce3 Audio (rev a2)
00:06.1 Modem: nVidia Corporation nForce3 Audio (rev a2)
00:08.0 IDE interface: nVidia Corporation nForce3 IDE (rev a5)
00:0a.0 PCI bridge: nVidia Corporation nForce3 PCI Bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation nForce3 AGP Bridge (rev a4)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 420 Go 32M] (rev a3)
02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:04.0 CardBus bridge: Texas Instruments PCI1620 PC Card Controller (rev 01)
02:04.1 CardBus bridge: Texas Instruments PCI1620 PC Card Controller (rev 01)
02:04.2 System peripheral: Texas Instruments PCI1620 Firmware Loading Function (rev 01)



The wireless button does not turn on.  It was working with Windows.  A few post said that it doesn't matter.  However, I do have a wireless card built in!  All these fixes I guess would work if BroadCom showed up, but it doesnt! Can someone help me?  My PCMCIA cards don't work (I guess that's the other problem with these computers) so I have no wireless even that way... I had to used wired to get online which is quite frustrating.

---

### Post by sexynjig on 2008-10-19
btw... I installed  the suggested drivers... but you can see it doesn't have the hardware...


/etc$ sudo ndiswrapper -l
 
bcmwl5 : driver installed
bcmwl5a : driver installed

and iwconfig...

lo        no wireless extensions.

eth0      no wireless extensions.

---

### Post by sexynjig on 2008-10-19
bump

---

### Post by sexynjig on 2008-10-20
^^^

---

