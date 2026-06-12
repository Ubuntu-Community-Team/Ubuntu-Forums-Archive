---
title: "Projector Toshiba on Ubuntu 12.04"
date: 2014-08-30
forum: Hardware
---

### Post by radopenev on 2014-08-30
I'm having a problem with old projector Toshiba TDP-S35, when connecting to laptop ASUS P50W. Fresh install ubuntu 12.04 and 

$ lshw -c display

*-display:0             
       description: VGA compatible controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:44 memory:fe400000-fe7fffff memory:d0000000-dfffffff ioport:dc00(size=8)
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:fe800000-fe8fffff


my xrandr output is:

Screen 0: minimum 320 x 200, current 2166 x 768, maximum 8192 x 8192
LVDS1 connected 1366x768+0+0 (normal left inverted right x axis y axis) 344mm x 194mm
   1366x768       60.0*+
   1360x768       59.8     60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 connected 800x600+1366+168 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0  
   800x600        60.3*    56.2  
   848x480        60.0  
   640x480        59.9  
HDMI1 disconnected (normal left inverted right x axis y axis)
DP1 disconnected (normal left inverted right x axis y axis)
DP2 disconnected (normal left inverted right x axis y axis)

Displays tool tell me UNKNOWN display. 
Fn+F8 switched between displays and resolution changed correctly (mirror mod is "on" by default), but nothing on projector. When test input signal (pressing input button), projector recognize signal :(

Sugestion? ):P
p.s. 
$ dmesg | grep vga
[    0.200824] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.200840] vgaarb: loaded
[    0.200841] vgaarb: bridge control possible 0000:00:02.0
[   18.138567] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem

$ lspci -vv
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 09) (prog-if 00 [VGA controller])
	Subsystem: ASUSTeK Computer Inc. Device 1862
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 44
	Region 0: Memory at fe400000 (64-bit, non-prefetchable) [size=4M]
	Region 2: Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Region 4: I/O ports at dc00 [size=8]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: <access denied>
	Kernel driver in use: i915
	Kernel modules: i915

00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 09)
	Subsystem: ASUSTeK Computer Inc. Device 1862
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Region 0: Memory at fe800000 (64-bit, non-prefetchable) [size=1M]
	Capabilities: <access denied>

---

### Post by radopenev on 2014-09-02
Please a little help? Any ideas!!!
The situation on 14.04 is the same :(

---

