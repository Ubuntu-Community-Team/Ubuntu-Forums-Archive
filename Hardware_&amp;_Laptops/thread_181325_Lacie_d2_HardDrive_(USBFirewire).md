---
title: "Lacie d2 HardDrive (USB/Firewire)"
date: 2006-05-24
forum: Hardware &amp; Laptops
---

### Post by sporniket on 2006-05-24
Hi,

Until last week I was running Ubuntu 4.10 and it was working well with Lacie d2 HardDrive on USB2.

However when I upgraded from 4.10 to 5.04 then 5.10, it does not work anymore with USB2 (see dmesg output). Fortunately, it turns out that it work using FireWire (good surprise !).

I couldn't find an answer to my problem (why does it not work on USB ?? How to fix ??) and I'm a bit worried by some messages in dmesg when plugging using FireWire.

First the dmesg output when using USB, then when using FireWire. Thanks in advance

```
[4294838.837000] usb 5-3: new high speed USB device using ehci_hcd and address 2
[4294838.927000] scsi1 : SCSI emulation for USB Mass Storage devices
[4294838.930000] usb-storage: device found at 2
[4294838.930000] usb-storage: waiting for device to settle before scanning
[4294843.931000]   Vendor: WDC WD16  Model: 00BB-00FTA0       Rev: 15.0
[4294843.931000]   Type:   Direct-Access                      ANSI SCSI revision: 04
[4294843.950000] SCSI device sdb: 312581808 512-byte hdwr sectors (160042 MB)
[4294843.950000] sdb: assuming drive cache: write through
[4294843.954000] SCSI device sdb: 312581808 512-byte hdwr sectors (160042 MB)
[4294843.954000] sdb: assuming drive cache: write through
[4294843.954000]  /dev/scsi/host1/bus0/target0/lun0: p1 p2
[4294843.969000] Attached scsi disk sdb at scsi1, channel 0, id 0, lun 0
[4294920.033000] usb 5-3: reset high speed USB device using ehci_hcd and address 2
[4294923.095000] usb 5-3: device descriptor read/64, error -110
[4294938.258000] usb 5-3: device descriptor read/64, error -110
[4294938.421000] usb 5-3: reset high speed USB device using ehci_hcd and address 2
[4294941.483000] usb 5-3: device descriptor read/64, error -110
[4294956.646000] usb 5-3: device descriptor read/64, error -110
[4294956.809000] usb 5-3: reset high speed USB device using ehci_hcd and address 2
[4294961.822000] usb 5-3: device descriptor read/8, error -110
[4294966.934000] usb 5-3: device descriptor read/8, error -110
[4294967.097000] usb 5-3: reset high speed USB device using ehci_hcd and address 2
[4294972.109000] usb 5-3: device descriptor read/8, error -110
[4294977.221000] usb 5-3: device descriptor read/8, error -110
[4294977.322000] scsi: Device offlined - not ready after error recovery: host 1 channel 0 id 0 lun 0
[4294977.322000] scsi1 (0:0): rejecting I/O to offline device
[4294977.322000] Buffer I/O error on device sdb, logical block 0
[4294977.322000] Buffer I/O error on device sdb, logical block 1
[4294977.322000] Buffer I/O error on device sdb, logical block 2
[4294977.322000] Buffer I/O error on device sdb, logical block 3
[4294977.322000] Buffer I/O error on device sdb, logical block 4
[4294977.322000] Buffer I/O error on device sdb, logical block 5
[4294977.322000] Buffer I/O error on device sdb, logical block 6
[4294977.322000] Buffer I/O error on device sdb, logical block 7
[4294977.322000] usb 5-3: USB disconnect, address 2
[4294977.323000] scsi1 (0:0): rejecting I/O to offline device
[4294977.323000] scsi1 (0:0): rejecting I/O to offline device
[4294977.325000] scsi1 (0:0): rejecting I/O to offline device
[4294977.325000] Buffer I/O error on device sdb, logical block 0
[4294977.326000] usb-storage: device scan complete
[4294977.625000] usb 5-3: new high speed USB device using ehci_hcd and address 3
[4294980.687000] usb 5-3: device descriptor read/64, error -110
[4294995.850000] usb 5-3: device descriptor read/64, error -110
[4294996.013000] usb 5-3: new high speed USB device using ehci_hcd and address 4
[4294999.078000] usb 5-3: device descriptor read/64, error -110
[4295014.241000] usb 5-3: device descriptor read/64, error -110
[4295014.404000] usb 5-3: new high speed USB device using ehci_hcd and address 5
[4295019.416000] usb 5-3: device descriptor read/8, error -110
[4295024.528000] usb 5-3: device descriptor read/8, error -110
[4295024.691000] usb 5-3: new high speed USB device using ehci_hcd and address 6
[4295029.703000] usb 5-3: device descriptor read/8, error -110
[4295034.815000] usb 5-3: device descriptor read/8, error -110

```

```
[4295976.913000] ieee1394: Error parsing configrom for node 0-01:1023
[4295976.913000] ieee1394: The root node is not cycle master capable; selecting a new root node and resetting...
[4295977.170000] ieee1394: Error parsing configrom for node 0-00:1023
[4295977.171000] ieee1394: Node changed: 0-00:1023 -> 0-01:1023
[4295984.320000] ieee1394: Node added: ID:BUS[0-00:1023]  GUID[00d04b491808fbc8]
[4295984.606000] sbp2: $Rev: 1219 $ Ben Collins <bcollins@debian.org>
[4295984.615000] scsi2 : SCSI emulation for IEEE-1394 SBP-2 Devices
[4295985.727000] ieee1394: sbp2: Logged into SBP-2 device
[4295985.727000] ieee1394: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[4295985.902000]   Vendor: WDC WD16  Model: 00BB-00FTA0       Rev: 15.0
[4295985.902000]   Type:   Direct-Access                      ANSI SCSI revision: 06
[4295985.920000] SCSI device sdb: 312581808 512-byte hdwr sectors (160042 MB)
[4295985.921000] sdb: asking for cache data failed
[4295985.921000] sdb: assuming drive cache: write through
[4295985.925000] SCSI device sdb: 312581808 512-byte hdwr sectors (160042 MB)
[4295985.926000] sdb: asking for cache data failed
[4295985.926000] sdb: assuming drive cache: write through
[4295985.926000]  /dev/scsi/host2/bus0/target0/lun0: p1 p2
[4295985.932000] Attached scsi disk sdb at scsi2, channel 0, id 0, lun 0
[4295987.314000] kjournald starting.  Commit interval 5 seconds
[4295987.315000] EXT3-fs warning: mounting fs with errors, running e2fsck is recommended
[4295987.316000] EXT3 FS on sdb2, internal journal
[4295987.316000] EXT3-fs: mounted filesystem with ordered data mode.

```

---

### Post by bobbb on 2006-05-26
Hi all, 

I have a similar problem :-? , maybe you can help me to go on with it: :) 

I can't mount anymore my external hard drives. 
I have two of them, that I initially used with Kubuntu. I can't see nor mount them anymore. They still show the windows partition under windows computers. 
I can still work with usb-keys. 
I don't know what happened, I beleive after an update (apt-get update/upgrade). I just updated the kernel (from 2.6.12.9 to 2.6.12.10) but no effect. Maybe I should downgrade? 

Filesystem is a linux one (not readable from windows). 
I would like to access my hard drive again! I would like to make a backup before upgrading to dapper, and for this, I need the hard drives! 
Harddrive have USB and Firewire access (same result). 

I have the same problem with the usb photocamera: it was seen, and now not anymore. 

Hereafter are some results after having plugged the drive: 

Thanks in advance, 

Bobbb


$ tail /var/log/messages: 
May 26 21:01:27 localhost kernel: [4294876.347000] usb 1-2: new full speed USB device using uhci_hcd and address 4
May 26 21:01:27 localhost kernel: [4294876.624000] Initializing USB Mass Storage driver...
May 26 21:01:27 localhost kernel: [4294876.629000] scsi0 : SCSI emulation for USB Mass Storage devices
May 26 21:01:27 localhost kernel: [4294876.630000] usbcore: registered new driver usb-storage
May 26 21:01:27 localhost kernel: [4294876.630000] USB Mass Storage support registered.
May 26 21:01:27 localhost usb.agent[8935]:      usb-storage: loaded successfully
May 26 21:01:56 localhost kernel: [4294905.713000] usb 1-2: reset full speed USB device using uhci_hcd and address 4
May 26 21:02:02 localhost kernel: [4294911.801000] scsi: Device offlined - not ready after error recovery: host 0 channel 0 id 0 lun 0

$ mount
/dev/hda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
usbfs on /proc/bus/usb type usbfs (rw)
tmpfs on /lib/modules/2.6.12-10-386/volatile type tmpfs (rw,mode=0755)
tmpfs on /dev type tmpfs (rw,size=10M,mode=0755)


For information: 
System: Kubuntu, Breezy, upgraded today. 

$ uname -a: 
Linux kubuntu 2.6.12-10-386 #1 Fri Apr 28 13:13:44 UTC 2006 i686 GNU/Linux

$ lsmod: 
scsi_mod              124872  3 usb_storage,sr_mod,sbp2
uhci_hcd               28048  0
usbcore               104316  5 usb_storage,ehci_hcd,uhci_hcd,usbhid

# sudo lspci -vv
0000:00:00.0 Host bridge: Intel Corp. 82855PM Processor to I/O Controller (rev 21)
        Subsystem: Wistron Corp.: Unknown device 4010
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Region 0: Memory at e0000000 (32-bit, prefetchable) [size=256M]
        Capabilities: [e4] #09 [4104]
        Capabilities: [a0] AGP version 2.0
                Status: RQ=32 Iso- ArqSz=0 Cal=0 SBA+ ITACoh- GART64- HTrans- 64bit- FW+ AGP3- Rate=x1,x2,x4
                Command: RQ=1 ArqSz=0 Cal=0 SBA- AGP- GART64- 64bit- FW- Rate=x1

0000:00:01.0 PCI bridge: Intel Corp. 82855PM Processor to AGP Controller (rev 21) (prog-if 00 [Normal decode])
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 96
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
        I/O behind bridge: 00003000-00003fff
        Memory behind bridge: d0100000-d01fffff
        Prefetchable memory behind bridge: d8000000-dfffffff
        BridgeCtl: Parity- SERR- NoISA+ VGA+ MAbort- >Reset- FastB2B-

0000:00:1d.0 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Wistron Corp.: Unknown device 4006
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin A routed to IRQ 11
        Region 4: I/O ports at 1800 [size=32]

0000:00:1d.1 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Wistron Corp.: Unknown device 4006
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin B routed to IRQ 10
        Region 4: I/O ports at 1820 [size=32]

0000:00:1d.2 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Wistron Corp.: Unknown device 4006
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin C routed to IRQ 11
        Region 4: I/O ports at 1840 [size=32]

0000:00:1d.7 USB Controller: Intel Corp. 82801DB/DBM (ICH4/ICH4-M) USB 2.0 EHCI Controller (rev 03) (prog-if 20 [EHCI])
        Subsystem: Wistron Corp.: Unknown device 1071
        Control: I/O- Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Interrupt: pin D routed to IRQ 10
        Region 0: Memory at d0000000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: [50] Power Management version 2
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=375mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-
        Capabilities: [58] #0a [2080]

0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev 83) (prog-if 00 [Normal decode])
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR+
        Latency: 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=32
        Memory behind bridge: d0200000-d02fffff
        BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-

0000:00:1f.0 ISA bridge: Intel Corp. 82801DBM LPC Interface Controller (rev 03)
        Control: I/O+ Mem+ BusMaster+ SpecCycle+ MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0

0000:00:1f.1 IDE interface: Intel Corp. 82801DBM (ICH4) Ultra ATA Storage Controller (rev 03) (prog-if 8a [Master SecP PriP])
        Subsystem: Wistron Corp.: Unknown device 4006
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin A routed to IRQ 11
        Region 0: I/O ports at <unassigned>
        Region 1: I/O ports at <unassigned>
        Region 2: I/O ports at <unassigned>
        Region 3: I/O ports at <unassigned>
        Region 4: I/O ports at 1860 [size=16]
        Region 5: Memory at 20000000 (32-bit, non-prefetchable) [size=1K]

0000:00:1f.3 SMBus: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
        Subsystem: Wistron Corp.: Unknown device 4006
        Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Interrupt: pin B routed to IRQ 10
        Region 4: I/O ports at 1880 [size=32]



==

---

