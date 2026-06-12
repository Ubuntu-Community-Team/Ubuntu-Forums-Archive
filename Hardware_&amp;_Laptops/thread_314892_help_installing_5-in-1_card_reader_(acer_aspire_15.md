---
title: "help installing 5-in-1 card reader (acer aspire 1520)"
date: 2006-12-08
forum: Hardware &amp; Laptops
---

### Post by abh83 on 2006-12-08
Can someone please help me install my card reader. I'm a newb to ubuntu/linux and i'm kinna lost! :( Help is greatly appreciated!!

dmesg | tail:

> [17188743.020000] hde: max request size: 128KiB
[17188743.020000] hde: 1947648 sectors (997 MB) w/1KiB Cache, CHS=3804/16/32
[17188743.020000] hde: cache flushes not supported
[17188743.020000]  hde:hde: status error: status=0x7f { DriveReady DeviceFault S eekComplete DataRequest CorrectedError Index Error }
[17188743.020000] hde: status error: error=0x00 { }
[17188743.020000] ide: failed opcode was: unknown
[17188743.020000] hde: drive not ready for command
[17188743.068000] ide2: reset: master: error (0x40?)
[17188743.072000]  hde1
[17188743.072000] ide-cs: hde: Vcc = 3.3, Vpp = 0.0


lspci:
> 
0000:00:00.0 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
0000:00:00.1 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
0000:00:00.2 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
0000:00:00.3 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
0000:00:00.4 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
0000:00:00.7 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
0000:00:0a.0 Ethernet controller: Linksys, A Division of Cisco Systems [AirConn] INPROCOMM IPN 2220 Wireless L AN Adapter (rev 01)
0000:00:0b.0 CardBus bridge: Texas Instruments PCI7420 CardBus Controller
0000:00:0b.1 CardBus bridge: Texas Instruments PCI7420 CardBus Controller
0000:00:0b.2 FireWire (IEEE 1394): Texas Instruments PCI7x20 1394a-2000 OHCI Two-Port PHY/Link-Layer Controlle r
0000:00:0c.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)
0000:00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
0000:00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
0000:00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
0000:00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
0000:00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (re v 06)
0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev  50)
0000:00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configu ration
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
0000:01:00.0 VGA compatible controller: nVidia Corporation NV34GLM [GeForce FX Go 5300] (rev a1)

Noteworthy:

it seems my system does recognize my card reader because i can actually see it show up in system-administration-disks
[IMG]http://i13.tinypic.com/4fy5qur.png[/IMG]

thx in advance!

---

### Post by abh83 on 2006-12-08
help anyone??

---

### Post by abh83 on 2006-12-11
lol I guess this is a real pain in the ***? ;)

---

