---
title: "PCMCIA troubles"
date: 2008-12-08
forum: Hardware
---

### Post by nosaje on 2008-12-08
Hi,

I have an old Sony PCG-N505SN upon which I have successfully installed Xubuntu 8.10.  I am experiencing a problem getting the wireless network card working.

Symptoms:  No network access, occasional freezes, unfriendly lines in logs (see below), occasional (brief) detection in the gui.

Hardware:  Cardbus is detected as Ricoh RL5c475, Wireless card detects as RaLink RT2500 (is a Belkin F5D7010 3000uk).  Hardware functions ok in windows.

I currently believe I have an IRQ problem as it looks like both the Ricoh and the RaLink get IRQ 9, but am struggling to fix it as the only advice I can find is for pcmcia-cs which is deprecated.

From dmesg:
rt2500pci 0000:01:00.0: PCI INT A -> Link[LNKB] -> GSI 9 (level, low) -> IRQ 9
rt2500pci 0000:01:00.0: setting latency timer to 64
rt2x00pci -> rt2x00pci_alloc_reg: Error - Failed to allocate registers.
rt2500pci 0000:01:00.0: PCI INT a disabled
rt2500pci: probe of 0000:01:00.0 failed with error -12

From lspci -vvv:
00:0c.0 CardBus bridge: Ricoh Co Ltd RL5c475 (rev 80)
	Subsystem: Sony Corporation Device 8061
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66Mhz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ >SERR- <PERR- INTx-
	Latency: 168
	Interrupt: pin A routed to IRQ 9
	Region 0: Memory at 18010000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=00, secondary=01, subordinate=04, sec-latency=176
	Memory window 0: 10000000-13fff000 (prefetchable)
	Memory window 1: 14000000-17fff000
	I/O window 0: 00001400-000014ff
	I/O window 1: 00001800-000018ff
	BridgeCtl: Parity- SERR- ISA- VGA- MAbort- >Reset- 15bInt- PostWrite+
	16-bit legacy interface ports at 0001
	Kernel driver in use: yenta_cardbus
	Kernel modules: yenta_socket

01:00.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)
	Subsystem: Belkin Device 701a
	Control: I/O- Mem- Busmaster- SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66Mhz- UDF- FastB2B- ParErr- DEVSEL=slow >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Interrupt: pin A routed to IRQ 9
	Region 0: Memory at <ignored> (32-bit, non-prefetchable) [disabled]
	Capabilities: <access denied>
	Kernel modules: rt2500pci

I have tried booting with noapic or acpi=off to no effect, and I have tried disabling printer, serial ports etc in the bios to keep it simple!

All suggestions appreciated.
Thanks

---

### Post by nosaje on 2008-12-09
Looks like this one has been reported as a bug.  Wish I knew how to get around it!

[https://bugs.launchpad.net/ubuntu/+source/rt2x00/+bug/189711](https://bugs.launchpad.net/ubuntu/+source/rt2x00/+bug/189711)

---

### Post by nosaje on 2008-12-10
OK, well I've put lots of time in and discovered.....

The problem is with the rt2x00pci drivers built into the Kernel shipped with Intrepid.

My solution so far is....

1. remove card
2. modprobe -r rt2500pci
3. download the rt2500 LEGACY code from rt2x00.serialmonkey.com and do a "make debug" on it
4. insmod rt2500.ko debug=31
5. kill nm-applet and do it manually at the command line, e.g.
     sudo iwconfig ra0 mode Managed
     sudo iwconfig ra0 essid "YOUR ESSID GOES HERE"
     sudo iwconfig ra0 up
     sudo dhclient ra0
   (will be more complex if you add authentication etc)

Now I just need to automate that somehow so I get the right module on boot and so kernel updates don't overwrite and then get nm-applet to talk to ra0 - any clues I'd be grateful!

---

### Post by nosaje on 2008-12-17
On testing this fix for a few days I find I get random drops.  
My solution was to go out and buy an Edimax USB stick (EW-7318USG) which works perfectly on my N505 without any trouble.  If anybody reads this with the same hardware as me I strongly recommend you just go the USB route.

---

