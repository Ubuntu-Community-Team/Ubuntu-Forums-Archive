---
title: "AMD 64 RT2500 driver woes"
date: 2005-03-23
forum: Hardware &amp; Laptops
---

### Post by narb on 2005-03-23
I have had this module working in Mandrake with the mandrake stock kernel and with compiled kernels. After ditching Mandrake and moved to AMD64 Kubuntu the driver module rt2500 will not register the interface with the kernel. It should be addressed as ra0.
 
 The module appears to compile cleanly and is installed in the correct /lib/modules/ tree. modprobe rt2500 doesn't give any errors and dmesg shows that the same PCI IRQ is getting assigned that is in lspci -v. 
 
 /etc/modprobe.d/rt2500 contains:
 alias ra0 rt2500
 
 when trying to bring up the interface:
 root@narghoul:/home/narb # ifconfig ra0 up
 ra0: ERROR while getting interface flags: No such device
 
 I have tried loading the kernels with PCI=routeirq with the same results.
 On a Sager 4750, AMD 64 3700+
 Anyone have any ideas?

---

### Post by barbarian on 2005-03-24
The same situation here..
Firstly, I was trying rt2500 via ndiswrapper then native linux rt200 version 1.1b2, but no luck..

ifconfig ra0:
EROR while getting interface flags: No such device

I took driver from [here](http://rt2x00.serialmonkey.com/wiki/index.php/Main_Page)  


My spec:
Fujitsu-Siemens Amilo A1640, AMD 3000+ mobile, 512DDRAM, CN-WF513 wireless lan adapter..

---

### Post by narb on 2005-03-24
I never even tried the ndiswrapper thing because it is pretty well documented that it will not work with the x86_64 architectures. Basically all ndiswrapper does is use a 32-bit windows driver for your 64-bit arch, meaning no worky. It would work if you were using the i386 version

---

### Post by narb on 2005-03-24
I have pretty much found out that for some reason the resources for the RT2500 cardbus aren't get set right by the kernel
lspci -vv shows:
-----
0000:00:05.0 Network controller: RaLink Ralink RT2500 802.11 Cardbus Reference Card (rev 01)
        Subsystem: Micro-Star International Co., Ltd.: Unknown device 6833
        Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=slow >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Interrupt: pin A routed to IRQ 16
        Region 0: Memory at <ignored> (32-bit, non-prefetchable) [disabled]
        Capabilities: <available only to root>
-----

the [disabled] part shows that there is a kernel-level problem.

and for the cardbus controller
----
0000:00:0c.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)
        Subsystem: CLEVO/KAPOK Computer: Unknown device 4701
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 168, Cache Line Size: 0x10 (64 bytes)
        Interrupt: pin A routed to IRQ 16
        Region 0: Memory at 40000000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=00, secondary=02, subordinate=05, sec-latency=176
        Memory window 0: 40400000-407ff000 (prefetchable)
        Memory window 1: 40800000-40bff000
        I/O window 0: 00004400-000044ff
        I/O window 1: 00004800-000048ff
        BridgeCtl: Parity- SERR- ISA- VGA- MAbort- >Reset+ 16bInt+ PostWrite+
        16-bit legacy interface ports at 0001
------


this may be a show-stopper for me, I am thinking about regressing to 32-bit

---

### Post by smo0th on 2008-03-14
I also have AMD 64 chipset and my rt2500 does not work, I'll try with the windows 64 drivers it's the only thing left at this moment.

---

### Post by smo0th on 2008-03-14
Tried the x64 windows drivers with ndiswrapper, no luck.

---

### Post by joez82 on 2008-05-03
Hello,
I've succesfully installed windows 64 bit drivers via ndiswrapper for my Linksys WMP54G wireless PCI board on my Ubuntu Hardy Heron AMD64 (8.04).
I've downloaded the drivers from: [http://files.aoaforums.com/I2130-RT2500V3.0.1.0_for_Win2003.zip.html](http://files.aoaforums.com/I2130-RT2500V3.0.1.0_for_Win2003.zip.html)

using the one inside the Win2003_AMD64 folder in the archive.

It works smoothly at full speed now.

---

### Post by fblade1987 on 2008-05-14
> **joez82 said:**
> Hello,
I've succesfully installed windows 64 bit drivers via ndiswrapper for my Linksys WMP54G wireless PCI board on my Ubuntu Hardy Heron AMD64 (8.04).
I've downloaded the drivers from: [http://files.aoaforums.com/I2130-RT2500V3.0.1.0_for_Win2003.zip.html](http://files.aoaforums.com/I2130-RT2500V3.0.1.0_for_Win2003.zip.html)

using the one inside the Win2003_AMD64 folder in the archive.

It works smoothly at full speed now.
The above method worked a treat My speeds is back to normal use this along side ndisgtk for any linux newbs and will work a treat REALLY WORKS WONDERS TRY IT

---

