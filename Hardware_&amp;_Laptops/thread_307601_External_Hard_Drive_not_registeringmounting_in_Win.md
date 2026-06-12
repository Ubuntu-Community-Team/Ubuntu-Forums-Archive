---
title: "External Hard Drive not registering/mounting in Windows/Linux?"
date: 2006-11-26
forum: Hardware &amp; Laptops
---

### Post by newagelink on 2006-11-26
I have a Western Digital external hard drive. Or I have an internal WD hard drive in an external enclosure. Otherwise, it's not Western Digital after all and I've been tricked (when mounting in Windows it shows up as 'WD' with some numbers, though.)

So I turn it on, and half the time Windows doesn't register it as a hard drive. It'll just say, "USB Device" and won't show up under My Computer.

In Linux, it seems to be doing the same thing; I guess you call it "mounting." I'll turn it on, nothing will seem to have happened, and I can't locate it in my Filesystem anywhere. (Where do I look?)

How can I manually mount it? Why isn't it registering with my computer? What does a USB external hard drive normally mount as?

What can I do? Does this make sense? ](*,) I'm disappointed; I paid $117 for it, 320 GB, from eBay, "New Unopened", and I currently have 70 GB of music on it.

I clicked System > Help > System Documentation > search "mount" > Ubuntu Desktop Guide > Configuring Your System > Hardware and am trying to figure it out ...

Maybe I should do homework first[,]("http://www.last.fm/user/newagelink/") in silence. :(

---

### Post by taurus on 2006-11-26
After you plug that harddrive in, what is the output of this command from a terminal?

```
dmesg | tail
```

---

### Post by newagelink on 2006-11-26
I just plugged it in and this time it registered and mounted. My music folder on the external hard drive, for example, is located here:
/media/DanielDrive/Music

So all external hard drives mount as "/media/[name]"?

---

### Post by taurus on 2006-11-26
The automount stuff will be mounted to /media/<name>.

---

### Post by newagelink on 2006-11-26
Mm.

... so should I go ahead with that command and post the output? (Thanks for your help!)

---

### Post by taurus on 2006-11-26
Your external harddrive already mounted, right!  Then, I don't need to see the output of that command since the automount did it job.

---

### Post by newagelink on 2006-11-26
But what do I do next time it doesn't automatically mount?

---

### Post by taurus on 2006-11-26
Then you need to look at that output and determine what device it is called, something like /dev/sda1, and mount it by hand...

```
sudo mount -t vfat /dev/sda1 /media/DanielDrive
```

---

### Post by newagelink on 2006-11-28
It did it again.
> **taurus said:**
> After you plug that harddrive in, what is the output of this command from a terminal?

```
dmesg | tail
``````
daniel@daniel-laptop:~$ dmesg | tail
[17250544.960000] usb 3-1: USB disconnect, address 4
[17258839.780000] usb 3-1: new high speed USB device using ehci_hcd and address 5
[17258839.912000] scsi1 : SCSI emulation for USB Mass Storage devices
[17258839.912000] usb-storage: device found at 5
[17258839.912000] usb-storage: waiting for device to settle before scanning
[17258844.916000]   Vendor:           Model:                   Rev:
[17258844.916000]   Type:   Direct-Access                      ANSI SCSI revisio n: 02
[17258844.928000] sd 1:0:0:0: Attached scsi disk sda
[17258844.928000] sd 1:0:0:0: Attached scsi generic sg0 type 0
[17258844.952000] usb-storage: device scan complete
daniel@daniel-laptop:~$

```Whoa ... what does all this mean ...? Where do I go to read about that dmesg command (and its output?)

---

### Post by newagelink on 2006-12-01
This time it's slightly different. It seems only the locations of the devices has changed -- although I don't know why they'd have changed, since I've not changed any of the USB ports.
```
daniel@daniel-laptop:~$ dmesg | tail
[17494430.324000] usb 3-1: USB disconnect, address 9
[17504394.392000] usb 3-1: new high speed USB device using ehci_hcd and address 10
[17504394.524000] scsi6 : SCSI emulation for USB Mass Storage devices
[17504394.524000] usb-storage: device found at 10
[17504394.524000] usb-storage: waiting for device to settle before scanning
[17504399.524000]   Vendor:           Model:                   Rev:
[17504399.524000]   Type:   Direct-Access                      ANSI SCSI revision: 02
[17504399.528000] sd 6:0:0:0: Attached scsi disk sda
[17504399.528000] sd 6:0:0:0: Attached scsi generic sg0 type 0
[17504399.528000] usb-storage: device scan complete
daniel@daniel-laptop:~$
```What does this mean ...? "Waiting for device to settle before scanning", but then it says "device scan complete" which I suppose means it settled down ... but if it's noticing that it's a "USB Mass Storage device", why isn't it mounting or existing? What does sd 6:0:0:0 mean, what is ... what do I do ...

---

### Post by newagelink on 2006-12-01
I think this is why I shouldn't enter commands into the Terminal without knowing what they do. I typed in "dmesg" and pressed enter accidentally without typing the " | tail" and got all this ... scary stuff:
```
mplete Error }
[17245847.896000] hdc: media error (bad sector): error=0x34 { AbortedCommand Las tFailedSense=0x03 }
[17245847.896000] ide: failed opcode was: unknown
[17245847.896000] end_request: I/O error, dev hdc, sector 919108
[17245847.944000] hdc: command error: status=0x51 { DriveReady SeekComplete Erro r }
[17245847.944000] hdc: command error: error=0x54 { AbortedCommand LastFailedSens e=0x05 }
[17245847.944000] ide: failed opcode was: unknown
[17245847.944000] end_request: I/O error, dev hdc, sector 919112
[17245847.996000] hdc: media error (bad sector): status=0x51 { DriveReady SeekCo mplete Error }
[17245847.996000] hdc: media error (bad sector): error=0x34 { AbortedCommand Las tFailedSense=0x03 }
[17245847.996000] ide: failed opcode was: unknown
[17245847.996000] end_request: I/O error, dev hdc, sector 919116
[17245848.064000] hdc: command error: status=0x51 { DriveReady SeekComplete Erro r }
[17245848.064000] hdc: command error: error=0x54 { AbortedCommand LastFailedSens e=0x05 }
[17245848.064000] ide: failed opcode was: unknown
[17245848.064000] end_request: I/O error, dev hdc, sector 919120
[17245848.172000] hdc: command error: status=0x51 { DriveReady SeekComplete Erro r }
[17245848.172000] hdc: command error: error=0x54 { AbortedCommand LastFailedSens e=0x05 }
[17245848.172000] ide: failed opcode was: unknown
[17245848.172000] end_request: I/O error, dev hdc, sector 918616
[17245848.224000] hdc: command error: status=0x51 { DriveReady SeekComplete Erro r }
[17245848.224000] hdc: command error: error=0x54 { AbortedCommand LastFailedSens e=0x05 }
[17245848.224000] ide: failed opcode was: unknown
[17245848.224000] end_request: I/O error, dev hdc, sector 918620
[17245848.272000] hdc: command error: status=0x51 { DriveReady SeekComplete Erro r }
[17245848.272000] hdc: command error: error=0x54 { AbortedCommand LastFailedSens e=0x05 }
[17245848.272000] ide: failed opcode was: unknown
[17245848.272000] end_request: I/O error, dev hdc, sector 918624
[17245848.324000] hdc: command error: status=0x51 { DriveReady SeekComplete Erro r }
[17245848.324000] hdc: command error: error=0x54 { AbortedCommand LastFailedSens e=0x05 }
[17245848.324000] ide: failed opcode was: unknown
[17245848.324000] end_request: I/O error, dev hdc, sector 918628
[17245848.376000] hdc: command error: status=0x51 { DriveReady SeekComplete Erro r }
[17245848.376000] hdc: command error: error=0x54 { AbortedCommand LastFailedSens e=0x05 }
[17245848.376000] ide: failed opcode was: unknown
[17245848.376000] end_request: I/O error, dev hdc, sector 918624
[17245848.424000] hdc: command error: status=0x51 { DriveReady SeekComplete Erro r }
[17245848.424000] hdc: command error: error=0x54 { AbortedCommand LastFailedSens e=0x05 }
[17245848.424000] ide: failed opcode was: unknown
[17245848.424000] end_request: I/O error, dev hdc, sector 918628
[17245848.476000] hdc: command error: status=0x51 { DriveReady SeekComplete Erro r }
[17245848.476000] hdc: command error: error=0x54 { AbortedCommand LastFailedSens e=0x05 }
[17245848.476000] ide: failed opcode was: unknown
[17245848.476000] end_request: I/O error, dev hdc, sector 918632
[17245848.528000] hdc: command error: status=0x51 { DriveReady SeekComplete Erro r }
[17245848.528000] hdc: command error: error=0x54 { AbortedCommand LastFailedSens e=0x05 }
[17245848.528000] ide: failed opcode was: unknown
[17245848.528000] end_request: I/O error, dev hdc, sector 918636
[17245848.580000] hdc: command error: status=0x51 { DriveReady SeekComplete Erro r }
[17245848.580000] hdc: command error: error=0x54 { AbortedCommand LastFailedSens e=0x05 }
[17245848.580000] ide: failed opcode was: unknown
[17245848.580000] end_request: I/O error, dev hdc, sector 918632
[17245848.632000] hdc: command error: status=0x51 { DriveReady SeekComplete Erro r }
[17245848.632000] hdc: command error: error=0x54 { AbortedCommand LastFailedSens e=0x05 }
[17245848.632000] ide: failed opcode was: unknown
[17245848.632000] end_request: I/O error, dev hdc, sector 918636
[17245848.680000] hdc: command error: status=0x51 { DriveReady SeekComplete Erro r }
[17245848.680000] hdc: command error: error=0x54 { AbortedCommand LastFailedSens e=0x05 }
[17245848.680000] ide: failed opcode was: unknown
[17245848.680000] end_request: I/O error, dev hdc, sector 918640
[17245848.732000] hdc: command error: status=0x51 { DriveReady SeekComplete Erro r }
[17245848.732000] hdc: command error: error=0x54 { AbortedCommand LastFailedSens e=0x05 }
[17245848.732000] ide: failed opcode was: unknown
[17245848.732000] end_request: I/O error, dev hdc, sector 918644
[17245848.784000] hdc: command error: status=0x51 { DriveReady SeekComplete Erro r }
[17245848.784000] hdc: command error: error=0x54 { AbortedCommand LastFailedSens e=0x05 }
[17245848.784000] ide: failed opcode was: unknown
[17245848.784000] end_request: I/O error, dev hdc, sector 918640
[17245848.832000] hdc: command error: status=0x51 { DriveReady SeekComplete Erro r }
[17245848.832000] hdc: command error: error=0x54 { AbortedCommand LastFailedSens e=0x05 }
[17245848.832000] ide: failed opcode was: unknown
[17245848.832000] end_request: I/O error, dev hdc, sector 918644
[17245848.884000] hdc: command error: status=0x51 { DriveReady SeekComplete Erro r }
[17245848.884000] hdc: command error: error=0x54 { AbortedCommand LastFailedSens e=0x05 }
[17245848.884000] ide: failed opcode was: unknown
[17245848.884000] end_request: I/O error, dev hdc, sector 918648
[17245848.984000] hdc: command error: status=0x51 { DriveReady SeekComplete Erro r }
[17245848.984000] hdc: command error: error=0x54 { AbortedCommand LastFailedSens e=0x05 }
[17245848.984000] ide: failed opcode was: unknown
[17245848.984000] end_request: I/O error, dev hdc, sector 918648
[17245849.044000] hdc: command error: status=0x51 { DriveReady SeekComplete Erro r }
[17245849.044000] hdc: command error: error=0x54 { AbortedCommand LastFailedSens e=0x05 }
[17245849.044000] ide: failed opcode was: unknown
[17245849.044000] end_request: I/O error, dev hdc, sector 918656
[17245849.164000] hdc: command error: status=0x51 { DriveReady SeekComplete Erro r }
[17245849.164000] hdc: command error: error=0x54 { AbortedCommand LastFailedSens e=0x05 }
[17245849.164000] ide: failed opcode was: unknown
[17245849.164000] end_request: I/O error, dev hdc, sector 918656
[17245849.232000] hdc: command error: status=0x51 { DriveReady SeekComplete Erro r }
[17245849.232000] hdc: command error: error=0x54 { AbortedCommand LastFailedSens e=0x05 }
[17245849.232000] ide: failed opcode was: unknown
[17245849.232000] end_request: I/O error, dev hdc, sector 918664
[17245849.336000] hdc: command error: status=0x51 { DriveReady SeekComplete Erro r }
[17245849.336000] hdc: command error: error=0x54 { AbortedCommand LastFailedSens e=0x05 }
[17245849.336000] ide: failed opcode was: unknown
[17245849.336000] end_request: I/O error, dev hdc, sector 918664
[17245849.388000] hdc: command error: status=0x51 { DriveReady SeekComplete Erro r }
[17245849.388000] hdc: command error: error=0x54 { AbortedCommand LastFailedSens e=0x05 }
[17245849.388000] ide: failed opcode was: unknown
[17245849.388000] end_request: I/O error, dev hdc, sector 918672
[17245849.488000] hdc: command error: status=0x51 { DriveReady SeekComplete Erro r }
[17245849.488000] hdc: command error: error=0x54 { AbortedCommand LastFailedSens e=0x05 }
[17245849.488000] ide: failed opcode was: unknown
[17245849.488000] end_request: I/O error, dev hdc, sector 918672
[17245849.540000] hdc: command error: status=0x51 { DriveReady SeekComplete Erro r }
[17245849.540000] hdc: command error: error=0x54 { AbortedCommand LastFailedSens e=0x05 }
[17245849.540000] ide: failed opcode was: unknown
[17245849.540000] end_request: I/O error, dev hdc, sector 918680
[17245849.640000] hdc: command error: status=0x51 { DriveReady SeekComplete Erro r }
[17245849.640000] hdc: command error: error=0x54 { AbortedCommand LastFailedSens e=0x05 }
[17245849.640000] ide: failed opcode was: unknown
[17245849.640000] end_request: I/O error, dev hdc, sector 918680
[17245849.692000] hdc: command error: status=0x51 { DriveReady SeekComplete Erro r }
[17245849.692000] hdc: command error: error=0x54 { AbortedCommand LastFailedSens e=0x05 }
[17245849.692000] ide: failed opcode was: unknown
[17245849.692000] end_request: I/O error, dev hdc, sector 918688
[17245849.812000] hdc: command error: status=0x51 { DriveReady SeekComplete Erro r }
[17245849.812000] hdc: command error: error=0x54 { AbortedCommand LastFailedSens e=0x05 }
[17245849.812000] ide: failed opcode was: unknown
[17245849.812000] end_request: I/O error, dev hdc, sector 918688
[17245849.860000] hdc: command error: status=0x51 { DriveReady SeekComplete Erro r }
[17245849.860000] hdc: command error: error=0x54 { AbortedCommand LastFailedSens e=0x05 }
[17245849.860000] ide: failed opcode was: unknown
[17245849.860000] end_request: I/O error, dev hdc, sector 918696
[17248495.432000] usb 3-1: new high speed USB device using ehci_hcd and address 4
[17248496.184000] Initializing USB Mass Storage driver...
[17248496.184000] scsi0 : SCSI emulation for USB Mass Storage devices
[17248496.184000] usb-storage: device found at 4
[17248496.184000] usb-storage: waiting for device to settle before scanning
[17248496.184000] usbcore: registered new driver usb-storage
[17248496.184000] USB Mass Storage support registered.
[17248501.184000]   Vendor: WDC WD32  Model:      WD-WCAMR177  Rev: 08.0
[17248501.184000]   Type:   Direct-Access                      ANSI SCSI revisio n: 02
[17248501.188000] usb-storage: device scan complete
[17248501.348000] Driver 'sd' needs updating - please use bus_type methods
[17248501.360000] SCSI device sda: 625142448 512-byte hdwr sectors (320073 MB)
[17248501.360000] sda: assuming drive cache: write through
[17248501.376000] SCSI device sda: 625142448 512-byte hdwr sectors (320073 MB)
[17248501.376000] sda: assuming drive cache: write through
[17248501.376000]  sda: sda1
[17248501.384000] sd 0:0:0:0: Attached scsi disk sda
[17248501.420000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[17248503.016000] printk: 59 messages suppressed.
[17248503.016000] NTFS-fs warning (device sda1): parse_options(): Option iochars et is deprecated. Please use option nls=<charsetname> in the future.
[17248503.216000] NTFS volume version 3.1.
[17250544.960000] usb 3-1: USB disconnect, address 4
[17258839.780000] usb 3-1: new high speed USB device using ehci_hcd and address 5
[17258839.912000] scsi1 : SCSI emulation for USB Mass Storage devices
[17258839.912000] usb-storage: device found at 5
[17258839.912000] usb-storage: waiting for device to settle before scanning
[17258844.916000]   Vendor:           Model:                   Rev:
[17258844.916000]   Type:   Direct-Access                      ANSI SCSI revisio n: 02
[17258844.928000] sd 1:0:0:0: Attached scsi disk sda
[17258844.928000] sd 1:0:0:0: Attached scsi generic sg0 type 0
[17258844.952000] usb-storage: device scan complete
[17259797.392000] usb 3-1: USB disconnect, address 5
[17263180.984000] ACPI: PCI interrupt for device 0000:02:00.0 disabled
[17263181.596000] ACPI: PCI interrupt for device 0000:02:04.0 disabled
[17263181.656000] ieee80211_crypt: unregistered algorithm 'NULL'
[17263181.660000] ieee80211_1_1_13_crypt: unregistered algorithm 'NULL'
[17263185.164000] Stopping tasks: ============================================== ======================================================|
[17263185.664000] Shrinking memory... done (69111 pages freed)
[17263214.360000] snd-usb-audio 2-2:1.2: no suspend for driver snd-usb-audio?
[17263214.360000] snd-usb-audio 2-2:1.1: no suspend for driver snd-usb-audio?
[17263214.980000] ACPI: PCI interrupt for device 0000:02:02.0 disabled
[17263214.980000] ACPI: PCI interrupt for device 0000:00:1f.5 disabled
[17263214.980000] ACPI: PCI interrupt for device 0000:00:1d.7 disabled
[17263214.996000] ACPI: PCI interrupt for device 0000:00:1d.1 disabled
[17263214.996000] ACPI: PCI interrupt for device 0000:00:1d.0 disabled
[17263214.996000] swsusp: Need to copy 57636 pages
[17263214.996000] swsusp: Restoring Highmem
[17304650.996000] **** SET: Misaligned resource pointer: d1f85ec2 Type 07 Len 0
[17304650.996000] **** SET: Misaligned resource pointer: d1f85ec2 Type 07 Len 0
[17304650.996000] **** SET: Misaligned resource pointer: d1f85ec2 Type 07 Len 0
[17304650.996000] **** SET: Misaligned resource pointer: d1f85ec2 Type 07 Len 0
[17304650.996000] **** SET: Misaligned resource pointer: d1f85ec2 Type 07 Len 0
[17304650.996000] **** SET: Misaligned resource pointer: d1f85ec2 Type 07 Len 0
[17304651.108000] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [LNKA] -> GSI 11 ( level, low) -> IRQ 11
[17304651.108000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> Link [LNKA] -> GSI 11 ( level, low) -> IRQ 11
[17304651.108000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[17304651.108000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> Link [LNKD] -> GSI 11 ( level, low) -> IRQ 11
[17304651.108000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[17304651.124000] PCI: Enabling device 0000:00:1d.7 (0000 -> 0002)
[17304651.124000] ACPI: PCI Interrupt 0000:00:1d.7[D] -> Link [LNKH] -> GSI 10 ( level, low) -> IRQ 10
[17304651.124000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[17304651.124000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[17304651.124000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> Link [LNKC] -> GSI 10 ( level, low) -> IRQ 10
[17304651.124000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKB] -> GSI 5 (l evel, low) -> IRQ 5
[17304651.124000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[17304651.376000] ACPI: PCI Interrupt 0000:02:02.0[A] -> Link [LNKA] -> GSI 11 ( level, low) -> IRQ 11
[17304651.376000] ACPI: PCI Interrupt 0000:02:02.2[C] -> Link [LNKC] -> GSI 10 ( level, low) -> IRQ 10
[17304651.376000] ACPI: PCI Interrupt 0000:02:02.4[A] -> Link [LNKA] -> GSI 11 ( level, low) -> IRQ 11
[17304652.164000] snd-usb-audio 2-2:1.1: no resume for driver snd-usb-audio?
[17304652.164000] snd-usb-audio 2-2:1.2: no resume for driver snd-usb-audio?
[17304652.164000] Restarting tasks... done
[17304652.180000] usb 1-2: USB disconnect, address 3
[17304652.420000] usb 1-2: new low speed USB device using uhci_hcd and address 4
[17304652.652000] input: Microsoft Microsoft Wireless Optical Mouse&#65533; 1.00 as /cl ***/input/input4
[17304652.652000] input: USB HID v1.11 Mouse [Microsoft Microsoft Wireless Optic al Mouse&#65533; 1.00] on usb-0000:00:1d.0-2
[17304652.668000] usb 2-2: USB disconnect, address 3
[17304666.316000] b44.c:v0.97 (Nov 30, 2005)
[17304666.316000] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [LNKD] -> GSI 11 ( level, low) -> IRQ 11
[17304666.324000] eth0: Broadcom 4400 10/100BaseT Ethernet 00:e0:b8:92:74:d6
[17304667.136000] ieee80211_1_1_13_crypt: registered algorithm 'NULL'
[17304667.152000] ieee80211_1_1_13: 802.11 data/management/control stack, 1.1.13
[17304667.152000] ieee80211_1_1_13: Copyright (C) 2004-2005 Intel Corporation <j ketreno@linux.intel.com>
[17304667.656000] ieee80211_crypt: registered algorithm 'NULL'
[17304668.056000] ieee80211: 802.11 data/management/control stack, git-1.1.7
[17304668.056000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno @linux.intel.com>
[17304668.344000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.1.1
[17304668.344000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[17304668.344000] Warning: PCI driver ipw2200 has a struct device_driver shutdow n method, please update!
[17304668.344000] ACPI: PCI Interrupt 0000:02:04.0[A] -> Link [LNKE] -> GSI 11 ( level, low) -> IRQ 11
[17304668.344000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[17304669.860000] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.1 1a channels)
[17304673.004000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[17304676.004000] b44: eth0: Link is up at 100 Mbps, full duplex.
[17304676.004000] b44: eth0: Flow control is off for TX and off for RX.
[17304676.004000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[17304678.540000] ACPI: Power Button (FF) [PWRF]
[17304678.540000] ACPI: Lid Switch [LID0]
[17304678.540000] ACPI: Sleep Button (CM) [SLPB]
[17304678.784000] ACPI: Fan [FAN1] (off)
[17304679.048000] ACPI: Thermal Zone [THRM] (37 C)
[17304679.828000] ACPI: AC Adapter [ACAD] (on-line)
[17304680.112000] ACPI: Battery Slot [BAT0] (battery present)
[17304686.884000] eth0: no IPv6 routers present
[17342721.020000] usb 2-2: new full speed USB device using uhci_hcd and address 4
[17344019.276000] usb 3-1: new high speed USB device using ehci_hcd and address 6
[17344019.408000] scsi2 : SCSI emulation for USB Mass Storage devices
[17344019.408000] usb-storage: device found at 6
[17344019.408000] usb-storage: waiting for device to settle before scanning
[17344024.412000]   Vendor:           Model:                   Rev:
[17344024.412000]   Type:   Direct-Access                      ANSI SCSI revisio n: 02
[17344024.420000] sd 2:0:0:0: Attached scsi disk sda
[17344024.420000] sd 2:0:0:0: Attached scsi generic sg0 type 0
[17344024.436000] usb-storage: device scan complete
[17344302.032000] usb 3-1: USB disconnect, address 6
[17345943.296000] usb 3-1: new high speed USB device using ehci_hcd and address 7
[17345943.428000] scsi3 : SCSI emulation for USB Mass Storage devices
[17345943.428000] usb-storage: device found at 7
[17345943.428000] usb-storage: waiting for device to settle before scanning
[17345948.428000]   Vendor:           Model:                   Rev:
[17345948.428000]   Type:   Direct-Access                      ANSI SCSI revisio n: 02
[17345948.428000] sd 3:0:0:0: Attached scsi disk sda
[17345948.428000] sd 3:0:0:0: Attached scsi generic sg0 type 0
[17345948.432000] usb-storage: device scan complete
[17346003.284000] usb 3-1: USB disconnect, address 7
[17346886.784000] usb 3-3: new high speed USB device using ehci_hcd and address 8
[17346886.916000] usb 3-3: configuration #1 chosen from 2 choices
[17346886.916000] scsi4 : SCSI emulation for USB Mass Storage devices
[17346886.916000] usb-storage: device found at 8
[17346886.916000] usb-storage: waiting for device to settle before scanning
[17346891.916000]   Vendor: Apple     Model: iPod              Rev: 1.62
[17346891.916000]   Type:   Direct-Access                      ANSI SCSI revisio n: 00
[17346891.916000] SCSI device sda: 117210239 512-byte hdwr sectors (60012 MB)
[17346891.920000] sda: Write Protect is off
[17346891.920000] sda: Mode Sense: 68 00 00 08
[17346891.920000] sda: assuming drive cache: write through
[17346891.920000] SCSI device sda: 117210239 512-byte hdwr sectors (60012 MB)
[17346891.920000] sda: Write Protect is off
[17346891.920000] sda: Mode Sense: 68 00 00 08
[17346891.920000] sda: assuming drive cache: write through
[17346891.920000]  sda: sda1 sda2
[17346891.932000] sd 4:0:0:0: Attached scsi removable disk sda
[17346891.932000] sd 4:0:0:0: Attached scsi generic sg0 type 0
[17346891.936000] usb-storage: device scan complete
[17346892.336000] Buffer I/O error on device sda2, logical block 58492664
[17346892.356000] Buffer I/O error on device sda2, logical block 58492664
[17346892.360000] Buffer I/O error on device sda2, logical block 58492664
[17346892.360000] Buffer I/O error on device sda2, logical block 58492664
[17346892.360000] Buffer I/O error on device sda2, logical block 58492664
[17346892.360000] Buffer I/O error on device sda2, logical block 58492664
[17346892.636000] Buffer I/O error on device sda2, logical block 58492664
[17346892.636000] Buffer I/O error on device sda2, logical block 58492664
[17346892.636000] Buffer I/O error on device sda2, logical block 58492664
[17346892.636000] Buffer I/O error on device sda2, logical block 58492664
[17346893.620000] FAT: utf8 is not a recommended IO charset for FAT filesystems,  filesystem will be case sensitive!
[17351099.984000] usb 3-3: USB disconnect, address 8
[17351151.004000] ACPI: PCI interrupt for device 0000:02:00.0 disabled
[17351151.376000] ACPI: PCI interrupt for device 0000:02:04.0 disabled
[17351151.432000] ieee80211_crypt: unregistered algorithm 'NULL'
[17351151.496000] ieee80211_1_1_13_crypt: unregistered algorithm 'NULL'
[17351155.640000] Stopping tasks: ============================================== =========================================================|
[17351155.736000] Shrinking memory... done (46102 pages freed)
[17351196.140000] snd-usb-audio 2-2:1.2: no suspend for driver snd-usb-audio?
[17351196.140000] snd-usb-audio 2-2:1.1: no suspend for driver snd-usb-audio?
[17351197.136000] ACPI: PCI interrupt for device 0000:02:02.0 disabled
[17351197.136000] ACPI: PCI interrupt for device 0000:00:1f.5 disabled
[17351197.136000] ACPI: PCI interrupt for device 0000:00:1d.7 disabled
[17351197.152000] ACPI: PCI interrupt for device 0000:00:1d.1 disabled
[17351197.152000] ACPI: PCI interrupt for device 0000:00:1d.0 disabled
[17351197.152000] swsusp: Need to copy 61196 pages
[17351197.152000] swsusp: Restoring Highmem
[17479204.152000] **** SET: Misaligned resource pointer: d1f85dc2 Type 07 Len 0
[17479204.152000] **** SET: Misaligned resource pointer: d1f85dc2 Type 07 Len 0
[17479204.152000] **** SET: Misaligned resource pointer: d1f85dc2 Type 07 Len 0
[17479204.152000] **** SET: Misaligned resource pointer: d1f85dc2 Type 07 Len 0
[17479204.152000] **** SET: Misaligned resource pointer: d1f85dc2 Type 07 Len 0
[17479204.152000] **** SET: Misaligned resource pointer: d1f85dc2 Type 07 Len 0
[17479204.748000] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [LNKA] -> GSI 11 ( level, low) -> IRQ 11
[17479204.748000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> Link [LNKA] -> GSI 11 ( level, low) -> IRQ 11
[17479204.748000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[17479204.748000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> Link [LNKD] -> GSI 11 ( level, low) -> IRQ 11
[17479204.748000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[17479204.764000] PCI: Enabling device 0000:00:1d.7 (0000 -> 0002)
[17479204.764000] ACPI: PCI Interrupt 0000:00:1d.7[D] -> Link [LNKH] -> GSI 10 ( level, low) -> IRQ 10
[17479204.764000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[17479204.764000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[17479204.764000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> Link [LNKC] -> GSI 10 ( level, low) -> IRQ 10
[17479204.764000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKB] -> GSI 5 (l evel, low) -> IRQ 5
[17479204.764000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[17479205.016000] ACPI: PCI Interrupt 0000:02:02.0[A] -> Link [LNKA] -> GSI 11 ( level, low) -> IRQ 11
[17479205.016000] ACPI: PCI Interrupt 0000:02:02.2[C] -> Link [LNKC] -> GSI 10 ( level, low) -> IRQ 10
[17479205.016000] ACPI: PCI Interrupt 0000:02:02.4[A] -> Link [LNKA] -> GSI 11 ( level, low) -> IRQ 11
[17479205.808000] snd-usb-audio 2-2:1.1: no resume for driver snd-usb-audio?
[17479205.808000] snd-usb-audio 2-2:1.2: no resume for driver snd-usb-audio?
[17479205.808000] Restarting tasks... done
[17479205.828000] usb 1-2: USB disconnect, address 4
[17479206.068000] usb 1-2: new low speed USB device using uhci_hcd and address 5
[17479206.300000] input: Microsoft Microsoft Wireless Optical Mouse&#65533; 1.00 as /cl ***/input/input5
[17479206.300000] input: USB HID v1.11 Mouse [Microsoft Microsoft Wireless Optic al Mouse&#65533; 1.00] on usb-0000:00:1d.0-2
[17479206.316000] usb 2-2: USB disconnect, address 4
[17479206.556000] usb 2-2: new full speed USB device using uhci_hcd and address 5
[17479222.680000] b44.c:v0.97 (Nov 30, 2005)
[17479222.680000] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [LNKD] -> GSI 11 ( level, low) -> IRQ 11
[17479222.684000] eth0: Broadcom 4400 10/100BaseT Ethernet 00:e0:b8:92:74:d6
[17479224.024000] ieee80211_1_1_13_crypt: registered algorithm 'NULL'
[17479224.040000] ieee80211_1_1_13: 802.11 data/management/control stack, 1.1.13
[17479224.040000] ieee80211_1_1_13: Copyright (C) 2004-2005 Intel Corporation <j ketreno@linux.intel.com>
[17479224.088000] ieee80211_crypt: registered algorithm 'NULL'
[17479224.664000] ieee80211: 802.11 data/management/control stack, git-1.1.7
[17479224.664000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno @linux.intel.com>
[17479224.960000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.1.1
[17479224.960000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[17479224.960000] Warning: PCI driver ipw2200 has a struct device_driver shutdow n method, please update!
[17479224.960000] ACPI: PCI Interrupt 0000:02:04.0[A] -> Link [LNKE] -> GSI 11 ( level, low) -> IRQ 11
[17479224.960000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[17479226.700000] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.1 1a channels)
[17479230.008000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[17479231.744000] ACPI: Power Button (FF) [PWRF]
[17479231.744000] ACPI: Lid Switch [LID0]
[17479231.744000] ACPI: Sleep Button (CM) [SLPB]
[17479232.100000] ACPI: Fan [FAN1] (off)
[17479232.212000] ACPI: Thermal Zone [THRM] (38 C)
[17479233.004000] b44: eth0: Link is up at 100 Mbps, full duplex.
[17479233.004000] b44: eth0: Flow control is off for TX and off for RX.
[17479233.004000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[17479233.036000] ACPI: AC Adapter [ACAD] (on-line)
[17479233.276000] ACPI: Battery Slot [BAT0] (battery present)
[17479243.568000] eth0: no IPv6 routers present
[17494329.764000] usb 3-1: new high speed USB device using ehci_hcd and address 9
[17494329.896000] scsi5 : SCSI emulation for USB Mass Storage devices
[17494329.896000] usb-storage: device found at 9
[17494329.896000] usb-storage: waiting for device to settle before scanning
[17494334.896000]   Vendor:           Model:                   Rev:
[17494334.896000]   Type:   Direct-Access                      ANSI SCSI revisio n: 02
[17494334.900000] sd 5:0:0:0: Attached scsi disk sda
[17494334.900000] sd 5:0:0:0: Attached scsi generic sg0 type 0
[17494334.900000] usb-storage: device scan complete
[17494430.324000] usb 3-1: USB disconnect, address 9
[17504394.392000] usb 3-1: new high speed USB device using ehci_hcd and address 10
[17504394.524000] scsi6 : SCSI emulation for USB Mass Storage devices
[17504394.524000] usb-storage: device found at 10
[17504394.524000] usb-storage: waiting for device to settle before scanning
[17504399.524000]   Vendor:           Model:                   Rev:
[17504399.524000]   Type:   Direct-Access                      ANSI SCSI revisio n: 02
[17504399.528000] sd 6:0:0:0: Attached scsi disk sda
[17504399.528000] sd 6:0:0:0: Attached scsi generic sg0 type 0
[17504399.528000] usb-storage: device scan complete
[17510733.716000] usb 3-1: USB disconnect, address 10
[17510954.452000] usb 2-2: USB disconnect, address 5
```
I plugged the USB drive into a different port and turned it on:
```
daniel@daniel-laptop:~$ dmesg | tail
[17504394.524000] scsi6 : SCSI emulation for USB Mass Storage devices
[17504394.524000] usb-storage: device found at 10
[17504394.524000] usb-storage: waiting for device to settle before scanning
[17504399.524000]   Vendor:           Model:                   Rev:
[17504399.524000]   Type:   Direct-Access                      ANSI SCSI revision: 02
[17504399.528000] sd 6:0:0:0: Attached scsi disk sda
[17504399.528000] sd 6:0:0:0: Attached scsi generic sg0 type 0
[17504399.528000] usb-storage: device scan complete
[17510733.716000] usb 3-1: USB disconnect, address 10
[17510954.452000] usb 2-2: USB disconnect, address 5
daniel@daniel-laptop:~$

```

---

### Post by newagelink on 2006-12-02
I'm not damaging the hard drive by turning it off then back on after it's not registering, am I?

---

### Post by newagelink on 2006-12-03
Now it makes a repeated weird clicking-etching sort of noise when it turns on; does anyone know what that means?

---

