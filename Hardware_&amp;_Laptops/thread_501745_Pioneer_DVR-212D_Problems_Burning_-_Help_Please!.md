---
title: "Pioneer DVR-212D Problems Burning - Help Please!"
date: 2007-07-15
forum: Hardware &amp; Laptops
---

### Post by BoGs on 2007-07-15
When I try burning cds / dvds.... I have yet to get a proper burn. It starts up and creates the iso image then when it comes down to actually burning it just crashes and pops out the cd/dvd I then put it in my other computer and the cd/dvd burns properly. I can read dvds / cds no problem.

I have tried the following (none have worked):
Sony CDR
Maxell DVD-R
Ridata DVD-R DL
TDK CDR
TDK DVD-R

Here is my lspci
```
00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 04)
00:01.0 PCI bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL PCI Express Root Port (rev 04)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7600 GS] (rev a1)
06:08.0 Ethernet controller: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller (rev 01)

```

I have tried using gnome baker and basero software.

If any help or ideas would be much appreciated.... Thanks!

---

### Post by gmaniac on 2007-07-15
Well, could you paste the output of the dmesg.
Also what program do you use for burning. The programs I have used are K3b and nero for linux. If you use one of those try starting them from the command line and see if they spew any error messages there. Also try burning in a low speed and see if that helps.

---

### Post by BoGs on 2007-07-15
command line for k3b

```
adding udi   /org/freedesktop/Hal/devices/volume_empty_cd_r
(K3bDevice::DeviceManager) request for empty device!
(K3bDevice::HalConnection) lock queued for /org/freedesktop/Hal/devices/storage_model_DVD_RW__DVR_212D
(K3bDevice::HalConnection) unlock queued for /org/freedesktop/Hal/devices/storage_model_DVD_RW__DVR_212D
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
removing udi /org/freedesktop/Hal/devices/volume_empty_cd_r
Launched ok, pid = 5758

```



and end of dmesg


```
[  230.267071] audit(1184539124.030:3): dev=tap0 prom=256 old_prom=0 auid=4294967295
[  230.269736] br0: port 2(tap0) entering learning state
[  240.719535] tap0: no IPv6 routers present
[  245.231844] br0: topology change detected, propagating
[  245.231850] br0: port 2(tap0) entering forwarding state
[ 4289.863696] cdrom: This disc doesn't have any tracks I recognize!

```

---

### Post by BoGs on 2007-07-15
I removed some settings from xorg.... and now i just get 


```
(K3bDevice::Device) /dev/scd0:  Number of supported write speeds via 2A: 6
(K3bDevice::Device) /dev/scd0 : 7056 KB/s
(K3bDevice::Device) /dev/scd0 : 5644 KB/s
(K3bDevice::Device) /dev/scd0 : 4233 KB/s
(K3bDevice::Device) /dev/scd0 : 2822 KB/s
(K3bDevice::Device) /dev/scd0 : 1764 KB/s
(K3bDevice::Device) /dev/scd0 : 705 KB/s
adding udi   /org/freedesktop/Hal/devices/volume_empty_cd_r
(K3bDevice::HalConnection) lock queued for /org/freedesktop/Hal/devices/storage_model_DVD_RW__DVR_212D
(K3bDevice::HalConnection) unlock queued for /org/freedesktop/Hal/devices/storage_model_DVD_RW__DVR_212D
removing udi /org/freedesktop/Hal/devices/volume_empty_cd_r
Launched ok, pid = 5674

```


and from gnomebaker...

```
wodim: No write mode specified.
wodim: Asuming -tao mode.
wodim: Future versions of wodim may have different drive dependent defaults.
scsidev: '3,0,0'
scsibus: 3 target: 0 lun: 0
Linux sg driver version: 3.5.34
Wodim version: 1.1.2
SCSI buffer size: 64512
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
TOC Type: 3 = CD-ROM XA mode 2
atapi: 1
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'PIONEER '
Identification : 'DVD-RW  DVR-212D'
Revision       : '1.09'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x0009 (CD-R)
Profile: 0x002B (DVD+R/DL) 
Profile: 0x001B (DVD+R) 
Profile: 0x001A (DVD+RW) 
Profile: 0x0016 (DVD-R/DL layer jump recording) 
Profile: 0x0015 (DVD-R/DL sequential recording) 
Profile: 0x0014 (DVD-RW sequential recording) 
Profile: 0x0013 (DVD-RW restricted overwrite) 
Profile: 0x0011 (DVD-R sequential recording) 
Profile: 0x0010 (DVD-ROM) 
Profile: 0x000A (CD-RW) 
Profile: 0x0009 (CD-R) (current)
Profile: 0x0008 (CD-ROM) 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 1267712 = 1238 KB
FIFO size      : 12582912 = 12288 KB
Speed set to 2822 KB/s
   4 seconds.   3 seconds.   2 seconds.   1 seconds.   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
Performing OPC...
Errno: 5 (Input/output error), send opc scsi sendcmd: no error
CDB:  54 01 00 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 04 00 00 46 DB 0E 00 00 00 00 44 D9 00 00
Sense Key: 0x4 Hardware Error, Segment 0
Sense Code: 0x44 Qual 0xD9 (internal target failure) [No matching qualifier] Fru 0x0
Sense flags: Blk 18139 (not valid) 
cmd finished after 15.473s timeout 60s
wodim: OPC failed.
Writing  time:   19.615s

```

---

