---
title: "HELP - USB devices not recognised"
date: 2009-03-02
forum: Hardware
---

### Post by broadbeans on 2009-03-02
I have just installed the 32bit 8.04 LTS version (using an original canonical dvd) on my 64bit AMD Athlon desktop and updated around 384 packages!  Everything went fine until it rebooted and kept on complaining about usb devices not accepting address.

Once it booted up, it doesn't detect any USB device. I have a logitech quickcam messenger and a HP Photosmart C3180 printer. Even it is refusing to recognise a usb pen drive! 

lsusb hangs forever and I've tried rmmod ehci_hcd to no avail

kernel version 2.6.24-23-generic

lspci output
```
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge
00:02.0 PCI bridge: ATI Technologies Inc RS480 PCI-X Root Port
00:11.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller
00:12.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 04)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: ATI Technologies Inc RV610 video device [Radeon HD 2400 PRO]
01:00.1 Audio device: ATI Technologies Inc RV610 audio device [Radeon HD 2400 PRO]
02:01.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)
02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:04.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)

```

Any help would be much appreciated.

---

### Post by broadbeans on 2009-03-02
If it helps,  dmesg | grep usb output before removing ehci_hcd:

```

[   28.348381] usbcore: registered new interface driver usbfs
[   28.348402] usbcore: registered new interface driver hub
[   28.364764] usbcore: registered new device driver usb
[   29.882656] usb usb1: configuration #1 chosen from 1 choice
[   30.046390] usb usb2: configuration #1 chosen from 1 choice
[   30.289987] usb 1-3: new full speed USB device using ohci_hcd and address 2
[   30.302064] usb usb3: configuration #1 chosen from 1 choice
[   30.725366] usb 3-5: new high speed USB device using ehci_hcd and address 2
[   30.862150] usb 3-5: configuration #1 chosen from 1 choice
[   30.877709] usbcore: registered new interface driver libusual
[   30.885861] usbcore: registered new interface driver usb-storage
[   30.885939] usb-storage: device found at 2
[   30.885941] usb-storage: waiting for device to settle before scanning
[   35.878491] usb-storage: device scan complete
[   41.063386]  [<f88edccb>] usb_hcd_irq+0x2b/0x60 [usbcore]
[   41.063492] [<f88edca0>] (usb_hcd_irq+0x0/0x60 [usbcore])
[   41.063510] [<f88edca0>] (usb_hcd_irq+0x0/0x60 [usbcore])
[   41.063528] [<f88edca0>] (usb_hcd_irq+0x0/0x60 [usbcore])
[  117.257842] usb 3-5: reset high speed USB device using ehci_hcd and address 2
[  132.811163] usb 3-5: device not accepting address 2, error -110
[  132.923135] usb 3-5: reset high speed USB device using ehci_hcd and address 2
[  148.476502] usb 3-5: device not accepting address 2, error -110
[  148.588473] usb 3-5: reset high speed USB device using ehci_hcd and address 2
[  159.018809] usb 3-5: device not accepting address 2, error -110
[  159.130781] usb 3-5: reset high speed USB device using ehci_hcd and address 2
[  169.561110] usb 3-5: device not accepting address 2, error -110
[  169.561207] usb 3-5: USB disconnect, address 2
[  169.673091] usb 3-5: new high speed USB device using ehci_hcd and address 3
[  185.226404] usb 3-5: device not accepting address 3, error -110
[  185.338375] usb 3-5: new high speed USB device using ehci_hcd and address 4
[  200.891732] usb 3-5: device not accepting address 4, error -110
[  201.003697] usb 3-5: new high speed USB device using ehci_hcd and address 5
[  211.433710] usb 3-5: device not accepting address 5, error -110
[  211.545675] usb 3-5: new high speed USB device using ehci_hcd and address 6
[  221.975647] usb 3-5: device not accepting address 6, error -110
[ 6836.665327] usb 3-5: new high speed USB device using ehci_hcd and address 7
[ 3805.017674] usb 3-5: device not accepting address 7, error -110
[ 3805.129527] usb 3-5: new high speed USB device using ehci_hcd and address 8
[ 3820.662931] usb 3-5: device not accepting address 8, error -110
[ 3820.774764] usb 3-5: new high speed USB device using ehci_hcd and address 9
[ 6904.129284] usb 3-5: device not accepting address 9, error -110
[ 6904.241247] usb 3-5: new high speed USB device using ehci_hcd and address 10
[ 6916.652342] usb 3-5: device not accepting address 10, error -110
[ 7006.484563] usb usb3: USB disconnect, address 1
[ 7009.538766] usb 1-3: new full speed USB device using ohci_hcd and address 3

```

---

### Post by broadbeans on 2009-03-07
Surprised to see no replies not even the ones that usually say "search before you post it..." sort of answers!

I've opened the box and disconnected the usb cables (both my cardreader and external ports) and it doesn't give any error messages upon booting. But this leaves me unable to use any usb device on ubuntu ](*,)  seriously thinking to dual boot xp as it was working in xp before i took the plunge and installed ubuntu (should've kept xp as well)

---

