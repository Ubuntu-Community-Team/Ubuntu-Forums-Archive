---
title: "SD Reader not working on Presario R3200"
date: 2010-06-25
forum: Hardware
---

### Post by Chlorhydrikk on 2010-06-25
Hello,
I own a laptop Compaq Presario R3200 that will not read my SD card... I tried lsusb but the reader is not displayed...
Could someone help me?

---

### Post by efflandt on 2010-06-26
Is this an external USB card reader, or a memory card slot in the laptop itself.  The latter is probably not USB (different type of block device).

Check the tail end of **dmesg** after a card is inserted, or output of **lshw**.

See if you get any errors in **dmesg | less** about trying to read a floppy that does not exist (that can interfere with auto mounting USB or CD/DVD).

---

### Post by Chlorhydrikk on 2010-06-26
Thank you very much for your answer,
It is an integrated card reader.
I don't really understand what dmesg and lshw said, but I think that the card reader is just not recognized by Ubuntu... How could I fix that?

---

### Post by IcarusR on 2010-06-26
Put a card in the reader then in terminal type

```
dmesg
```

& check the last 10 or so lines to see if it recognises a card has been inserted or are any errors. 
If you do not understand output post last 10 lines. 

To get a list of all pci (encludes your card reader) component details in a terminal type

```
lspci
```

Post lspci output to help us help you.

---

### Post by Chlorhydrikk on 2010-06-26
Okay.
I typed dmesg and nothing about the SD card!

Here's what I get with lspci:

```
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
01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 440 Go 64M] (rev a3)
02:00.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
02:04.0 CardBus bridge: Texas Instruments PCI1620 PC Card Controller (rev 01)
02:04.1 CardBus bridge: Texas Instruments PCI1620 PC Card Controller (rev 01)
02:04.2 System peripheral: Texas Instruments PCI1620 Firmware Loading Function (rev 01) 
```

---

### Post by IcarusR on 2010-06-27
I don't see a SD reader mentioned here. So I'm guessing that Ubuntu does not recognise it at all & therefore may be difficult to get working.
Suggest you get a USB card reader, they are cheap.

---

### Post by Chlorhydrikk on 2010-06-27
Well I prefer sticking with Windows in that case ;)
Thank you for your help anyway !

---

