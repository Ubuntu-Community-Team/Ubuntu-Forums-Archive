---
title: "PCI wireless adapter issues"
date: 2012-07-14
forum: Hardware
---

### Post by bboyblaq on 2012-07-14
Hi guys, brand new to Ubuntu, running 12.04 LTS

Heres my issue, I installed a PCI wireless adapter (TRENDnet TEW-643PI) I couldnt get a connection.

I installed ndiswrapper without a connection (headache) and installed the drivers for the wireless card, still, nothing.

LSPCI GIVES ME:

00:00.0 Host bridge: Intel Corporation 82875P/E7210 Memory Controller Hub (rev 02) 
00:01.0 PCI bridge: Intel Corporation 82875P Processor to AGP Controller (rev 02) 
00:06.0 System peripheral: Intel Corporation 82875P/E7210 Processor to I/O Memory Interface (rev 02) 
00:1d.0 USB controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02) 
00:1d.1 USB controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02) 
00:1d.2 USB controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02) 
00:1d.3 USB controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02) 
00:1d.7 USB controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02) 
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2) 
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02) 
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02) 
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02) 
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02) 
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02) 
01:00.0 VGA compatible controller: NVIDIA Corporation NV34 [GeForce FX 5200] (rev a1) 
02:01.0 Modem: Intel Corporation FA82537EP 56K V.92 Data/Fax Modem PCI (rev 04) 
02:02.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8190 802.11n Wireless LAN 
02:08.0 Ethernet controller: Intel Corporation 82562EZ 10/100 Ethernet Controller (rev 02) 


lshw -c network GIVES ME:

 *-network:0 UNCLAIMED   
       description: Network controller 
       product: RTL8190 802.11n Wireless LAN 
       vendor: Realtek Semiconductor Co., Ltd. 
       physical id: 2 
       bus info: pci@0000:02:02.0 
       version: 00 
       width: 32 bits 
       clock: 33MHz 
       capabilities: pm bus_master cap_list 
       configuration: latency=64 maxlatency=64 mingnt=32 
       resources: ioport:de00(size=256) memory:fcffe000-fcffefff 






Thanks in advance guys

---

### Post by ahallubuntu on 2012-07-14
I changed my mind, I don't think the 8192 driver I posted first will work - removed...

You might try emailing Realtek support and asking them for a solution.  You have a Realtek RTL8190 controller...

---

### Post by bboyblaq on 2012-07-14
> **ahallubuntu said:**
> I changed my mind, I don't think the 8192 driver I posted first will work - removed...

You might try emailing Realtek support and asking them for a solution.  You have a Realtek RTL8190 controller...

The 8192 driver wont work because I've tried to install the realtek driver too...  Thx for reading dude.

---

### Post by ahallubuntu on 2012-07-14
It's not clear exactly all that you've done, but it sounds like you've only tried to install the Windows driver via ndiswrapper.

Realtek provides native Linux driver source code (you have to build it) on their website for various chipsets.  I have used the 8192CU driver for a $6 USB dongle I've bought on eBay and it works great.  But I don't even see a driver listed for the 8190.  It's probably some variation of the 8192.  That's why I suggested you email Realtek directly.  Native drivers are a better solution than ndiswrapper if that's an option.

---

### Post by bboyblaq on 2012-07-14
> **ahallubuntu said:**
> It's not clear exactly all that you've done, but it sounds like you've only tried to install the Windows driver via ndiswrapper.

Realtek provides native Linux driver source code (you have to build it) on their website for various chipsets.  I have used the 8192CU driver for a $6 USB dongle I've bought on eBay and it works great.  But I don't even see a driver listed for the 8190.  It's probably some variation of the 8192.  That's why I suggested you email Realtek directly.  Native drivers are a better solution than ndiswrapper if that's an option.

All I've done is install the windows drivers via ndiswrapper.  I did check for a Linux native driver which I could not find, Thx for your suggestion to email Realtek i might just.

---

### Post by bboyblaq on 2012-07-16
Xp it is!

---

### Post by ahallubuntu on 2012-07-17
It's a shame people trying Linux for the first time don't understand that Linux developers don't have unlimited resources and that some hardware is better supported in Linux by its manufacturers than others.  It appears this TrendNET wireless card just wasn't supported  in Linux.  Blame the hardware manufacturer, not Linux or Ubuntu.

I only spend my money to support hardware that has good Linux support, which is why Ubuntu runs great on my computers.  In any case, a new wireless card that is Linux compatible is not expensive to buy, easily under $10 USD.

---

