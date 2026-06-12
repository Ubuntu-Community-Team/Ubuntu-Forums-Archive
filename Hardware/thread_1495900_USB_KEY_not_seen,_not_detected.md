---
title: "USB KEY not seen, not detected"
date: 2010-05-28
forum: Hardware
---

### Post by mal_conductor on 2010-05-28
I plug in USB memory and USMmem is not detected.

Something is wrong with the memory key.  It is not detected on any computer (windows or ubuntu).

Here is what happened:  I copied a move on this mem key, transferred the movie file to a secod PC.  At the other PC I deleted the move file.  I think I may have unplugged the USB key before it was OK to do so (second PC did not have remove USB icon).

Now this USB key is not detected at all.

Can some one suggest a fix.  Note reformatting does not work because PC does not see USBkey in the first place.

---

### Post by Joe of loath on 2010-05-28
what's the output of lsusb and dmesg after it's plugged in?

---

### Post by mal_conductor on 2010-05-28
> **Joe of loath said:**
> what's the output of lsusb and dmesg after it's plugged in?

Joe,

here is the output:

(Before plugging in)

ubuntu@FUJITSU:~$ lsusb
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 08ff:2580 AuthenTec, Inc. 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 046d:c016 Logitech, Inc. M-UV69a Optical Wheel Mouse
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

(After plugged in)

ubuntu@FUJITSU:~$ lsusb
Bus 005 Device 006: ID 1005:b113 Apacer Technology, Inc. Handy Steno 2.0 (256MB)
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 08ff:2580 AuthenTec, Inc. 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 046d:c016 Logitech, Inc. M-UV69a Optical Wheel Mouse
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
ubuntu@FUJITSU:~$ 



===========================

[   27.557991] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:00/input/input8
[   27.568198] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   29.102510] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 16 (level, low) -> IRQ 16
[   29.102541] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   30.691667] cs: IO port probe 0x100-0x3af: clean.
[   30.693529] cs: IO port probe 0x3e0-0x4ff: clean.
[   30.694304] cs: IO port probe 0x820-0x8ff: clean.
[   30.694948] cs: IO port probe 0xc00-0xcf7: clean.
[   30.695795] cs: IO port probe 0xa00-0xaff: clean.
[   30.700375] ipw2200: Detected geography ZZB (11 802.11bg channels, 13 802.11a channels)
[   30.942879] lp: driver loaded but no devices found
[   31.278775] Adding 417648k swap on /dev/sda6.  Priority:-1 extents:1 across:417648k
[   31.348759] EXT3 FS on sda5, internal journal
[   31.876548] ip_tables: (C) 2000-2006 Netfilter Core Team
[   32.156912] No dock devices found.
[   32.190105] ACPI: \_SB_.PCI0.SATA.PRID.P_D0: found ejectable bay
[   32.190115] ACPI: \_SB_.PCI0.SATA.PRID.P_D0: Adding notify handler
[   32.190155] ACPI: Error installing bay notify handler
[   32.190159] ACPI: Bay [\_SB_.PCI0.SATA.PRID.P_D0] Added
[   33.128050] apm: BIOS not found.
[   33.177663] ppdev: user-space parallel port driver
[   33.210868] audit(1275080107.956:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5020 profile="/usr/sbin/cupsd" namespace="default"
[   66.525658] Marking TSC unstable due to: cpufreq changes.
[   67.724842] eth0: link down
[   50.956594] Bluetooth: Core ver 2.11
[   50.957390] NET: Registered protocol family 31
[   50.957397] Bluetooth: HCI device and connection manager initialized
[   50.957404] Bluetooth: HCI socket layer initialized
[   34.081185] Bluetooth: L2CAP ver 2.9
[   34.081191] Bluetooth: L2CAP socket layer initialized
[   34.123206] Bluetooth: RFCOMM socket layer initialized
[   34.123222] Bluetooth: RFCOMM TTY layer initialized
[   34.123225] Bluetooth: RFCOMM ver 1.8
[   35.621196] [drm] Initialized drm 1.1.0 20060810
[   35.625849] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
[   35.625861] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   35.625946] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   80.800172] NET: Registered protocol family 10
[   80.801127] lo: Disabled Privacy Extensions
[   80.802402] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   87.296033] eth1: no IPv6 routers present
[   47.276521] NET: Registered protocol family 17
[   48.245662] ieee80211_crypt: registered algorithm 'WEP'
[  108.300024] eth1: no IPv6 routers present
[  116.527219] usb 5-1: new high speed USB device using ehci_hcd and address 4
[  116.564833] usb 5-1: configuration #1 chosen from 1 choice
[   58.399813] usbcore: registered new interface driver libusual
[   58.452584] Initializing USB Mass Storage driver...
[   58.472333] scsi4 : SCSI emulation for USB Mass Storage devices
[   58.473625] usbcore: registered new interface driver usb-storage
[   58.473817] USB Mass Storage support registered.
[   58.474080] usb-storage: device found at 4
[   58.474084] usb-storage: waiting for device to settle before scanning
[  117.588105] usb-storage: device scan complete
[  117.588905] scsi 4:0:0:0: Direct-Access              USB FLASH DRIVE  PMAP PQ: 0 ANSI: 0 CCS
[  117.613191] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[  117.613290] sd 4:0:0:0: Attached scsi generic sg2 type 0
[  138.719565] usb 5-2: new high speed USB device using ehci_hcd and address 5
[  138.757331] usb 5-2: configuration #1 chosen from 1 choice
[  138.807947] scsi5 : SCSI emulation for USB Mass Storage devices
[   69.409320] usb-storage: device found at 5
[   69.409325] usb-storage: waiting for device to settle before scanning
[   71.776958] usb-storage: device scan complete
[   71.777958] scsi 5:0:0:0: Direct-Access     Generic  Flash Disk       8.00 PQ: 0 ANSI: 2
[   71.789810] sd 5:0:0:0: [sdc] 33554432 512-byte hardware sectors (17180 MB)
[   71.790791] sd 5:0:0:0: [sdc] Write Protect is off
[   71.790797] sd 5:0:0:0: [sdc] Mode Sense: 03 00 00 00
[   71.790801] sd 5:0:0:0: [sdc] Assuming drive cache: write through
[   71.793790] sd 5:0:0:0: [sdc] 33554432 512-byte hardware sectors (17180 MB)
[   71.794664] sd 5:0:0:0: [sdc] Write Protect is off
[   71.794671] sd 5:0:0:0: [sdc] Mode Sense: 03 00 00 00
[   71.794675] sd 5:0:0:0: [sdc] Assuming drive cache: write through
[   71.794682]  sdc: sdc1
[   72.503249] sd 5:0:0:0: [sdc] Attached SCSI removable disk
[   72.503315] sd 5:0:0:0: Attached scsi generic sg3 type 0
[  217.160778] usb 5-1: USB disconnect, address 4
[  217.391975] usb 5-2: USB disconnect, address 5
[  218.700416] usb 5-1: new high speed USB device using ehci_hcd and address 6
[  218.741602] usb 5-1: configuration #1 chosen from 1 choice
[  218.790653] scsi6 : SCSI emulation for USB Mass Storage devices
[  218.798756] usb-storage: device found at 6
[  218.798766] usb-storage: waiting for device to settle before scanning
[  219.522046] usb-storage: device scan complete
[  219.522840] scsi 6:0:0:0: Direct-Access              USB FLASH DRIVE  PMAP PQ: 0 ANSI: 0 CCS
[  219.547257] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[  219.547358] sd 6:0:0:0: Attached scsi generic sg2 type 0
ubuntu@FUJITSU:~$

---

### Post by Joe of loath on 2010-05-28
OK, looks like it's been detected. What's the output of "sudo fdisk -l"?

---

### Post by mal_conductor on 2010-05-28
> **Joe of loath said:**
> OK, looks like it's been detected. What's the output of "sudo fdisk -l"?


ubuntu@FUJITSU:~$ sudo fdisk -l
[sudo] password for ubuntu: 

Disk /dev/sda: 30.0 GB, 30005821440 bytes
255 heads, 63 sectors/track, 3648 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x524f6b51

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2588    20788078+   7  HPFS/NTFS
/dev/sda2            2589        3648     8514450    5  Extended
/dev/sda5            2589        3596     8096728+  83  Linux
/dev/sda6            3597        3648      417658+  82  Linux swap / Solaris

---

### Post by Joe of loath on 2010-05-28
ok, what about "sudo fdisk -l /dev/sdb"?

---

### Post by mal_conductor on 2010-05-28
> **Joe of loath said:**
> ok, what about "sudo fdisk -l /dev/sdb"?

ubuntu@FUJITSU:~$ sudo fdisk -l /dev/sdb
[sudo] password for ubuntu: 
ubuntu@FUJITSU:~$ sudo fdisk -l /dev/sdb
ubuntu@FUJITSU:~$ 


=========

---

### Post by Joe of loath on 2010-05-28
Hmm, ok, doesn't seem to be registering the USB stick as a storage device, even though it does in dmesg.

I'm afraid I'm out of luck, someone with more experience will have to step in. If all it needed was a tweak to get it recognised I know how to pull files off it no trouble, but I don't know enough to fix this, sorry :(

EDIT: You did do those with it plugged in, right?

---

### Post by mal_conductor on 2010-05-28
> **Joe of loath said:**
> Hmm, ok, doesn't seem to be registering the USB stick as a storage device, even though it does in dmesg.

I'm afraid I'm out of luck, someone with more experience will have to step in. If all it needed was a tweak to get it recognised I know how to pull files off it no trouble, but I don't know enough to fix this, sorry :(

EDIT: You did do those with it plugged in, right?

Yeah, key was plugged in.  I did it a few times and with other keys to make sure that I was doing it right.  I reached the same conclusion you did.  Thank you for your help.

I have looked up some data recovery places that talk about removing the chip and reading it on a different reader. The cost is too much, I don't have that kind of money.

---

### Post by mal_conductor on 2010-05-28
ubuntu@FUJITSU:~$ lsusb
Bus 005 Device 007: ID 090c:1000 Feiya Technology Corp. Memory Bar
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 08ff:2580 AuthenTec, Inc. 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 046d:c016 Logitech, Inc. M-UV69a Optical Wheel Mouse
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
ubuntu@FUJITSU:~$ sudo fdisk -l /dev/sdv
ubuntu@FUJITSU:~$ 


hmmm. ... interesting.

I plugged in a key that works.  I can read/write to this key.

ran the commands: lsusb and sudo fdisk -l /dev/sdv
results listed above.  Key does not show up, yet it is mounted and I can read/wite.

---

### Post by Joe of loath on 2010-05-28
it's probable you can get some data off, it's just I'm not clever enough to know now lol. Hopefully some one else will be along soon!

---

