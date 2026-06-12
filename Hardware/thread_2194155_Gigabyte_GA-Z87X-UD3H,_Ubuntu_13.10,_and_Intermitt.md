---
title: "Gigabyte GA-Z87X-UD3H, Ubuntu 13.10, and Intermittent External USB Drive Failure"
date: 2013-12-16
forum: Hardware
---

### Post by linux4me on 2013-12-16
I have a Rosewill RX35-AT-SU3 USB 3.0 external hard drive running a Western Digital 1 TB Black Series hard drive. It is formatted with LUKS. In versions of Ubuntu prior to 13.04, when I connected it to the PC I was prompted to unlock and mount it. Since then, I have to use Disks to unlock and mount the file system. It works fine on one PC, but on my new system running a Gigabyte GA-Z87X-UD3H, I'm having intermittent problems with it. I'm running a clean install of Ubuntu 13.10.

About 25% of the time, the external USB drive is recognized and I can unlock and mount the filesystem with no problems; however, 75% of the time the activity light comes on for several seconds, then it goes out, and the drive does not appear in Disks. When it did work, I managed to transfer about 160 GB of files and it managed a rate of 39.5 MB/s.

I've tried different USB ports with no change in behavior.

I looked at dmesg, and it looks like this when the drive fails to appear:

```
[  434.157058] usb 4-5.4: new SuperSpeed USB device number 4 using xhci_hcd
[  434.173025] usb 4-5.4: New USB device found, idVendor=152d, idProduct=0539
[  434.173034] usb 4-5.4: New USB device strings: Mfr=1, Product=11, SerialNumber=3
[  434.173039] usb 4-5.4: Product: USB3.0 Device
[  434.173043] usb 4-5.4: Manufacturer: JMicron
[  434.173046] usb 4-5.4: SerialNumber: BBA00000016B
[  434.173678] usb 4-5.4: Set SEL for device-initiated U1 failed.
[  439.177461] usb 4-5.4: Set SEL for device-initiated U2 failed.
```

At this point, I'm suspecting it may be something I have configured incorrectly in the BIOS, but I'm not sure where to look. 

XHCI mode is currently set to "Smart Auto," which the motherboard manual explains as, "This mode is available only when the BIOS supports the xHCI controller in the pre-boot environment. This mode is similar to Auto, but it adds the capability to route the ports to xHCI or EHCI according to setting used in previous boots (for non-G3 boot) in the pre-boot environment. This allows the use of USB 3.0 devices prior to OS boot. xHCI controller enabling and rerouting should follow the steps in Auto, when previous boot routs ports to EHCI. Note: This is the recommended mode when BIOS has xHCI pre-boot support. (Default)"

Can anyone point me in the right direction to resolve this?

---

### Post by linux4me on 2013-12-17
I got a little more information out of dmesg:

```
[ 4038.896383] usb 4-5.4: new SuperSpeed USB device number 4 using xhci_hcd
[ 4038.912318] usb 4-5.4: New USB device found, idVendor=152d, idProduct=0539
[ 4038.912327] usb 4-5.4: New USB device strings: Mfr=1, Product=11, SerialNumber=3
[ 4038.912332] usb 4-5.4: Product: USB3.0 Device
[ 4038.912336] usb 4-5.4: Manufacturer: JMicron
[ 4038.912339] usb 4-5.4: SerialNumber: BBA00000016B
[ 4038.912985] usb 4-5.4: Set SEL for device-initiated U1 failed.
[ 4043.918380] usb 4-5.4: Set SEL for device-initiated U2 failed.
[ 4044.004861] usb-storage 4-5.4:1.0: USB Mass Storage device detected
[ 4044.004892] scsi8 : usb-storage 4-5.4:1.0
[ 4049.009928] usb 4-5.4: Set SEL for device-initiated U1 failed.
[ 4054.017258] usb 4-5.4: Set SEL for device-initiated U2 failed.
[ 4054.017327] usbcore: registered new interface driver usb-storage
[ 4076.866539] usb 4-5.4: device not accepting address 4, error -22
[ 4076.885677] scsi 8:0:0:0: Device offlined - not ready after error recovery
[ 4076.885885] usb 4-5.4: USB disconnect, device number 4
[ 4076.885987] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff8801c5767d80
[ 4076.885989] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff8801c5767dc0
```

It looks like the line:

```
device not accepting address 4, error -22
```

might help determine what the problem is, but I still haven't a clue what it means. The googling continues...

---

### Post by oldfred on 2013-12-17
Set SEL for device-initiated U1 failed

Google says that is related to power issues and USB3 ports. 
Is drive USB powered or separate?
Have you tried a USB2 port, but it will be slower?

[http://www.spinics.net/lists/linux-usb/msg93249.html](http://www.spinics.net/lists/linux-usb/msg93249.html)

Seems to even be a Windows issue.
[http://blogs.msdn.com/b/usbcoreblog/archive/2012/07/13/common-issues-in-usb-3-0-devices.aspx](http://blogs.msdn.com/b/usbcoreblog/archive/2012/07/13/common-issues-in-usb-3-0-devices.aspx)

---

### Post by linux4me on 2013-12-17
Thanks, oldfred. I just found the cure and was logging on to post it when I saw your message.

I saw those links, too. The drive does have its own power source, so a low-powered USB port should not be the issue. I did try it on other USB 3.0 ports on this machine, but it has no USB 2.0 ports. The drive mounts and works fine on other 13.10 installs via USB 2.0 ports.

What I found works is to change the setting XHCI mode in the BIOS from "Smart Auto" to "disabled." Ubuntu uses EHCI then, and the drive is recognized and works again.

Here's dmesg with a failure while XHCI is on "Smart Auto:"
```
[ 4038.896383] usb 4-5.4: new SuperSpeed USB device number 4 using xhci_hcd
[ 4038.912318] usb 4-5.4: New USB device found, idVendor=152d, idProduct=0539
[ 4038.912327] usb 4-5.4: New USB device strings: Mfr=1, Product=11, SerialNumber=3
[ 4038.912332] usb 4-5.4: Product: USB3.0 Device
[ 4038.912336] usb 4-5.4: Manufacturer: JMicron
[ 4038.912339] usb 4-5.4: SerialNumber: BBA00000016B
[ 4038.912985] usb 4-5.4: Set SEL for device-initiated U1 failed.
[ 4043.918380] usb 4-5.4: Set SEL for device-initiated U2 failed.
[ 4044.004861] usb-storage 4-5.4:1.0: USB Mass Storage device detected
[ 4044.004892] scsi8 : usb-storage 4-5.4:1.0
[ 4049.009928] usb 4-5.4: Set SEL for device-initiated U1 failed.
[ 4054.017258] usb 4-5.4: Set SEL for device-initiated U2 failed.
[ 4054.017327] usbcore: registered new interface driver usb-storage
[ 4076.866539] usb 4-5.4: device not accepting address 4, error -22
[ 4076.885677] scsi 8:0:0:0: Device offlined - not ready after error recovery
[ 4076.885885] usb 4-5.4: USB disconnect, device number 4
[ 4076.885987] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff8801c5767d80
[ 4076.885989] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff8801c5767dc0
```

And here is dmesg with XHCI set to "disabled," in which case the drive works:
```
[   50.781732] usb 2-1.5.4: new high-speed USB device number 6 using ehci-pci
[   50.890636] usb 2-1.5.4: New USB device found, idVendor=152d, idProduct=0539
[   50.890637] usb 2-1.5.4: New USB device strings: Mfr=1, Product=11, SerialNumber=3
[   50.890639] usb 2-1.5.4: Product: USB3.0 Device
[   50.890639] usb 2-1.5.4: Manufacturer: JMicron
[   50.890640] usb 2-1.5.4: SerialNumber: BBA00000016B
[   50.930747] usb-storage 2-1.5.4:1.0: USB Mass Storage device detected
[   50.930774] scsi8 : usb-storage 2-1.5.4:1.0
[   50.930815] usbcore: registered new interface driver usb-storage
[   51.931447] scsi 8:0:0:0: Direct-Access     Generic  USB3.0                PQ: 0 ANSI: 2 CCS
[   51.931653] sd 8:0:0:0: Attached scsi generic sg2 type 0
[   51.932279] sd 8:0:0:0: [sdb] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[   51.933259] sd 8:0:0:0: [sdb] Write Protect is off
[   51.933261] sd 8:0:0:0: [sdb] Mode Sense: 28 00 00 00
[   51.934268] sd 8:0:0:0: [sdb] No Caching mode page found
[   51.934269] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[   51.936886] sd 8:0:0:0: [sdb] No Caching mode page found
[   51.936888] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[   52.225750]  sdb: sdb1
[   52.230705] sd 8:0:0:0: [sdb] No Caching mode page found
[   52.230707] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[   52.230708] sd 8:0:0:0: [sdb] Attached SCSI disk
```

I guess that's the workaround. Now I need to figure out what the difference is between XHCI AND EHCI, and why the former lists the drive as "Super Speed" and the latter lists it as "High Speed," though they both recognize it as USB 3.0. I wasn't getting USB 3.0 speeds the rare times it mounted with XHCI, anyway.

Thanks for taking the time to reply.

---

### Post by linux4me on 2013-12-17
Bummer. According to [Wikipedia]("http://en.wikipedia.org/wiki/EHCI#EHCI"), EHCI is the older host controller standard and doesn't support Super Speed USB 3.0. XHCI is the new standard that provides better power efficiency, performance, and Super Speed USB 3.0.

So maybe this is a bug with XHCI in Ubuntu.

---

### Post by linux4me on 2013-12-18
I've got a workaround, so I can access my data, but I'm not satisfied. I want USB 3.0 speeds!

I'm starting to think this might be a problem with the Rosewill RX35-AT-SU3 rather than my motherboard or Ubuntu. 

I tested the only other USB 3.0 device I have, which is a Transcend flash drive, but it is recognized and automounts at USB 3.0 SuperSpeed.

I did (even more) Googling and found some reports that the Rosewill has a reputation for failed USB 3.0 connections and it looks like it is currently off the market, though a similar USB 2.0 version is still for sale. Unfortunately, mine is way out of warranty, so I doubt Rosewill will be any help. I have been happily using it for three years on USB 2.0 machines, so the problem--other than the failure to automount--has never come up until now, when I got a USB 3.0 machine, and I guess I have gotten my money's worth out of it. 

I'm going to try to get hold of a USB 3.0 dock and give it a try to see if it works.

---

### Post by sj26 on 2014-02-09
I have a [Zotac Zbox ID41]("http://www.zotacusa.com/zbox-id41.html") and a [Hotway HFD1-SU3S2 4 Bay Docking Station]("http://www.pccasegear.com/index.php?main_page=product_info&cPath=210_177_287&products_id=19272") and am having exactly the same problem.

Here's my logs:

```
Feb 10 01:04:29 blaster kernel: [46318.924845] usb 7-3: reset SuperSpeed USB device number 8 using xhci_hcd
Feb 10 01:04:29 blaster kernel: [46318.940870] usb 7-3: device firmware changed
Feb 10 01:04:29 blaster kernel: [46318.940981] usb 7-3: USB disconnect, device number 8
Feb 10 01:04:29 blaster kernel: [46318.940997] sd 9:0:0:1: Device offlined - not ready after error recovery
Feb 10 01:04:29 blaster kernel: [46318.941016] sd 9:0:0:1: [sdf] Unhandled error code
Feb 10 01:04:29 blaster kernel: [46318.941023] sd 9:0:0:1: [sdf]
Feb 10 01:04:29 blaster kernel: [46318.941029] Result: hostbyte=DID_ABORT driverbyte=DRIVER_OK
Feb 10 01:04:29 blaster kernel: [46318.941036] sd 9:0:0:1: [sdf] CDB:
Feb 10 01:04:29 blaster kernel: [46318.941041] Read(10): 28 20 e8 e0 88 00 00 00 08 00
Feb 10 01:04:29 blaster kernel: [46318.941066] end_request: I/O error, dev sdf, sector 3907028992
Feb 10 01:04:29 blaster kernel: [46318.941137] Buffer I/O error on device sdf, logical block 488378624
...
lots of:
Feb 10 01:04:29 blaster kernel: [46318.946013] sd 9:0:0:1: rejecting I/O to offline device
...
Feb 10 01:04:29 blaster kernel: [46318.959824] xhci_hcd 0000:01:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff880121482e00
Feb 10 01:04:29 blaster kernel: [46318.959841] xhci_hcd 0000:01:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff880121482e40
Feb 10 01:04:30 blaster kernel: [46319.792567] usb 7-3: new SuperSpeed USB device number 9 using xhci_hcd
Feb 10 01:04:30 blaster kernel: [46319.809297] usb 7-3: New USB device found, idVendor=152d, idProduct=0539
Feb 10 01:04:30 blaster kernel: [46319.809306] usb 7-3: New USB device strings: Mfr=1, Product=2, SerialNumber=5
Feb 10 01:04:30 blaster kernel: [46319.809312] usb 7-3: Product: USB to ATA/ATAPI Bridge
Feb 10 01:04:30 blaster kernel: [46319.809317] usb 7-3: Manufacturer: JMicron
Feb 10 01:04:30 blaster kernel: [46319.809322] usb 7-3: SerialNumber: 152D20551000
Feb 10 01:04:30 blaster kernel: [46319.810434] usb-storage 7-3:1.0: USB Mass Storage device detected
Feb 10 01:04:30 blaster kernel: [46319.810714] scsi10 : usb-storage 7-3:1.0
Feb 10 01:04:31 blaster kernel: [46320.808616] scsi 10:0:0:0: Direct-Access     WDC WD10 EAVS-00D7B1           PQ: 0 ANSI: 2 CCS
Feb 10 01:04:31 blaster kernel: [46320.808974] scsi 10:0:0:1: Direct-Access     ST2000VX 000-1CU164            PQ: 0 ANSI: 2 CCS
Feb 10 01:04:31 blaster kernel: [46320.809313] scsi 10:0:0:2: Direct-Access     ST4000DM 000-1F2168            PQ: 0 ANSI: 2 CCS
Feb 10 01:04:31 blaster kernel: [46320.810055] sd 10:0:0:0: Attached scsi generic sg1 type 0
Feb 10 01:04:31 blaster kernel: [46320.810972] sd 10:0:0:1: Attached scsi generic sg2 type 0
Feb 10 01:04:31 blaster kernel: [46320.811669] sd 10:0:0:2: Attached scsi generic sg3 type 0
Feb 10 01:04:31 blaster kernel: [46320.814832] sd 10:0:0:1: [sdc] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
Feb 10 01:04:31 blaster kernel: [46320.815012] sd 10:0:0:0: [sdb] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
Feb 10 01:04:31 blaster kernel: [46320.816139] sd 10:0:0:1: [sdc] Write Protect is off
... etc.
```

Here's verbose lspci:

```
00:00.0 Host bridge: Intel Corporation Atom Processor D4xx/D5xx/N4xx/N5xx DMI Bridge (rev 02)
        Subsystem: ZOTAC International (MCO) Ltd. Device a140
        Flags: bus master, fast devsel, latency 0
        Capabilities: [e0] Vendor Specific Information: Len=08 <?>

00:1b.0 Audio device: Intel Corporation NM10/ICH7 Family High Definition Audio Controller (rev 02)
        Subsystem: ZOTAC International (MCO) Ltd. Device a140
        Flags: bus master, fast devsel, latency 0, IRQ 44
        Memory at fe8fc000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
        Capabilities: [60] MSI: Enable+ Count=1/1 Maskable- 64bit+
        Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
        Capabilities: [100] Virtual Channel
        Capabilities: [130] Root Complex Link
        Kernel driver in use: snd_hda_intel

00:1c.0 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 1 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 00001000-00001fff
        Memory behind bridge: fe900000-fe9fffff
        Prefetchable memory behind bridge: 00000000c0000000-00000000c01fffff
        Capabilities: [40] Express Root Port (Slot+), MSI 00
        Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
        Capabilities: [90] Subsystem: ZOTAC International (MCO) Ltd. Device a140
        Capabilities: [a0] Power Management version 2
        Capabilities: [100] Virtual Channel
        Capabilities: [180] Root Complex Link
        Kernel driver in use: pcieport

00:1c.1 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 2 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        I/O behind bridge: 00002000-00002fff
        Memory behind bridge: fea00000-feafffff
        Prefetchable memory behind bridge: 00000000c0200000-00000000c03fffff
        Capabilities: [40] Express Root Port (Slot+), MSI 00
        Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
        Capabilities: [90] Subsystem: ZOTAC International (MCO) Ltd. Device a140
        Capabilities: [a0] Power Management version 2
        Capabilities: [100] Virtual Channel
        Capabilities: [180] Root Complex Link
        Kernel driver in use: pcieport

00:1c.2 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 3 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        I/O behind bridge: 0000d000-0000dfff
        Memory behind bridge: fcf00000-fdffffff
        Prefetchable memory behind bridge: 00000000ce000000-00000000dfffffff
        Capabilities: [40] Express Root Port (Slot+), MSI 00
        Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
        Capabilities: [90] Subsystem: ZOTAC International (MCO) Ltd. Device a140
        Capabilities: [a0] Power Management version 2
        Capabilities: [100] Virtual Channel
        Capabilities: [180] Root Complex Link
        Kernel driver in use: pcieport

00:1d.0 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
        Subsystem: ZOTAC International (MCO) Ltd. Device a140
        Flags: bus master, medium devsel, latency 0, IRQ 23
        I/O ports at cc00 [size=32]
        Kernel driver in use: uhci_hcd

00:1d.1 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
        Subsystem: ZOTAC International (MCO) Ltd. Device a140
        Flags: bus master, medium devsel, latency 0, IRQ 19
        I/O ports at c880 [size=32]
        Kernel driver in use: uhci_hcd

00:1d.2 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI])
        Subsystem: ZOTAC International (MCO) Ltd. Device a140
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at c800 [size=32]
        Kernel driver in use: uhci_hcd

00:1d.3 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #4 (rev 02) (prog-if 00 [UHCI])
        Subsystem: ZOTAC International (MCO) Ltd. Device a140
        Flags: bus master, medium devsel, latency 0, IRQ 16
        I/O ports at c480 [size=32]
        Kernel driver in use: uhci_hcd

00:1d.7 USB controller: Intel Corporation NM10/ICH7 Family USB2 EHCI Controller (rev 02) (prog-if 20 [EHCI])
        Subsystem: ZOTAC International (MCO) Ltd. Device a140
        Flags: bus master, medium devsel, latency 0, IRQ 23
        Memory at fe8fbc00 (32-bit, non-prefetchable) [size=1K]
        Capabilities: [50] Power Management version 2
        Capabilities: [58] Debug port: BAR=1 offset=00a0
        Kernel driver in use: ehci-pci

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=04, sec-latency=32
        I/O behind bridge: 0000e000-0000efff
        Memory behind bridge: feb00000-febfffff
        Capabilities: [50] Subsystem: ZOTAC International (MCO) Ltd. Device a140

00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
        Subsystem: ZOTAC International (MCO) Ltd. Device a140
        Flags: bus master, medium devsel, latency 0
        Capabilities: [e0] Vendor Specific Information: Len=0c <?>
        Kernel driver in use: lpc_ich

00:1f.2 IDE interface: Intel Corporation NM10/ICH7 Family SATA Controller [IDE mode] (rev 02) (prog-if 8f [Master SecP SecO PriP PriO])
        Subsystem: ZOTAC International (MCO) Ltd. Device a140
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
        I/O ports at b880 [size=8]
        I/O ports at c400 [size=4]
        I/O ports at c080 [size=8]
        I/O ports at c000 [size=4]
        I/O ports at bc00 [size=16]
        Memory at fe8fb800 (32-bit, non-prefetchable) [size=1K]
        Capabilities: [70] Power Management version 2
        Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation NM10/ICH7 Family SMBus Controller (rev 02)
        Subsystem: ZOTAC International (MCO) Ltd. Device a140
        Flags: medium devsel, IRQ 15
        I/O ports at 0400 [size=32]

01:00.0 USB controller: VIA Technologies, Inc. VL80x xHCI USB 3.0 Controller (rev 03) (prog-if 30 [XHCI])
        Subsystem: ZOTAC International (MCO) Ltd. Device 3432
        Physical Slot: 32
        Flags: bus master, fast devsel, latency 0, IRQ 43
        Memory at fe9ff000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [80] Power Management version 3
        Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit+
        Capabilities: [c4] Express Endpoint, MSI 00
        Capabilities: [100] Advanced Error Reporting
        Kernel driver in use: xhci_hcd

02:00.0 Network controller: Qualcomm Atheros Device 0037 (rev 01)
        Subsystem: AzureWave Device 1195
        Physical Slot: 33
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at fea80000 (64-bit, non-prefetchable) [size=512K]
        Expansion ROM at fea70000 [disabled] [size=64K]
        Capabilities: [40] Power Management version 2
        Capabilities: [50] MSI: Enable- Count=1/4 Maskable+ 64bit+
        Capabilities: [70] Express Endpoint, MSI 00
        Capabilities: [100] Advanced Error Reporting
        Capabilities: [140] Virtual Channel
        Capabilities: [160] Device Serial Number 00-00-00-00-00-00-00-00
        Kernel driver in use: ath9k

03:00.0 VGA compatible controller: NVIDIA Corporation GT218 [ION] (rev a2) (prog-if 00 [VGA controller])
        Subsystem: ZOTAC International (MCO) Ltd. Device 3100
        Physical Slot: 34
        Flags: bus master, fast devsel, latency 0, IRQ 18
        Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
        Memory at d0000000 (64-bit, prefetchable) [size=256M]
        Memory at ce000000 (64-bit, prefetchable) [size=32M]
        I/O ports at dc00 [size=128]
        Expansion ROM at fcf80000 [disabled] [size=512K]
        Capabilities: [60] Power Management version 3
        Capabilities: [68] MSI: Enable- Count=1/1 Maskable- 64bit+
        Capabilities: [78] Express Endpoint, MSI 00
        Capabilities: [b4] Vendor Specific Information: Len=14 <?>
        Capabilities: [100] Virtual Channel
        Capabilities: [128] Power Budgeting <?>
        Capabilities: [600] Vendor Specific Information: ID=0001 Rev=1 Len=024 <?>
        Kernel driver in use: nvidia

03:00.1 Audio device: NVIDIA Corporation High Definition Audio Controller (rev a1)
        Subsystem: ZOTAC International (MCO) Ltd. Device 3100
        Physical Slot: 34
        Flags: bus master, fast devsel, latency 0, IRQ 19
        Memory at fcf7c000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: [60] Power Management version 3
        Capabilities: [68] MSI: Enable- Count=1/1 Maskable- 64bit+
        Capabilities: [78] Express Endpoint, MSI 00
        Kernel driver in use: snd_hda_intel

04:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8110SC/8169SC Gigabit Ethernet (rev 10)
        Subsystem: Realtek Semiconductor Co., Ltd. RTL-8110SC/8169SC Gigabit Ethernet
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
        I/O ports at e800 [size=256]
        Memory at febdfc00 (32-bit, non-prefetchable) [size=256]
        Expansion ROM at febe0000 [disabled] [size=128K]
        Capabilities: [dc] Power Management version 2
        Kernel driver in use: r8169
```

I'll pop it into a USB2 slot for now, it seems like xhci is broken here, but it would be nice to get it running at full speed.

Worth noting, everything seemed fine until I added a third drive into the array, but removing a drive now doesn't seem to help.

I'm running latest saucy with updates, here's uname -a:

```
Linux blaster 3.11.0-15-generic #25-Ubuntu SMP Thu Jan 30 17:22:01 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by linux4me on 2014-02-09
I actually did end up filing a [bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1271268") for this, and was asked to file a bug report upstream, which I also did. I have received a couple of replies from the upstream report, but no resolution as yet.

My machine doesn't have any USB 2.0 ports or a spare USB 2.0 cable, so I am stuck either disabling XHCI in the BIOS or using another drive. I do have a WD 500 GB drive that will work with XHCI and USB 3.0 in the same Unitek dock that a 1 TB WD drive fails in.

---

