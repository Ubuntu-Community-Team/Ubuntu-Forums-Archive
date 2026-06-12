---
title: "How can I work with a USB HUB in ubuntu?"
date: 2009-04-20
forum: Hardware
---

### Post by krcabrer on 2009-04-20
Hi UBUNTU users and gurus:

I got a 4 port USB HUB 2.0 (coded as H4PU), but
it does not work like in window$.

How can I make it work on ubuntu?

Thank you for your help.

Kenneth

PS: If I type dmsg just after I connect the USB HUB,
the last lines are result:

> [175095.005052] usb 2-2: new high speed USB device using ehci_hcd and address 6
[175095.497396] usb 2-2: configuration #1 chosen from 1 choice
[175095.498109] scsi9 : SCSI emulation for USB Mass Storage devices
[175095.498346] usb-storage: device found at 6
[175095.498352] usb-storage: waiting for device to settle before scanning
[175100.496225] usb-storage: device scan complete
[175100.498501] scsi 9:0:0:0: Direct-Access     USB 2.0  USB Flash Drive  0.00 PQ: 0 ANSI: 2
[175100.501496] sd 9:0:0:0: [sdg] 63176704 512-byte hardware sectors (32346 MB)
[175100.502359] sd 9:0:0:0: [sdg] Write Protect is off
[175100.502365] sd 9:0:0:0: [sdg] Mode Sense: 00 00 00 00
[175100.502368] sd 9:0:0:0: [sdg] Assuming drive cache: write through
[175100.504983] sd 9:0:0:0: [sdg] 63176704 512-byte hardware sectors (32346 MB)
[175100.506359] sd 9:0:0:0: [sdg] Write Protect is off
[175100.506364] sd 9:0:0:0: [sdg] Mode Sense: 00 00 00 00
[175100.506367] sd 9:0:0:0: [sdg] Assuming drive cache: write through
[175100.506373]  sdg: sdg1
[175100.647643] sd 9:0:0:0: [sdg] Attached SCSI removable disk
[175100.647793] sd 9:0:0:0: Attached scsi generic sg7 type 0
[175110.478394] usb 2-2: USB disconnect, address 6
[175117.672025] usb 1-2: new full speed USB device using ohci_hcd and address 9
[175117.875205] usb 1-2: device descriptor read/all, error -62
[175118.056031] usb 1-2: new full speed USB device using ohci_hcd and address 10
[175118.640026] usb 1-2: device not accepting address 10, error -62
[175118.816043] usb 1-2: new full speed USB device using ohci_hcd and address 11
[175118.843206] usb 1-2: device descriptor read/8, error -62
[175118.968209] usb 1-2: device descriptor read/8, error -62
[175119.249035] usb 1-2: new full speed USB device using ohci_hcd and address 12
[175119.275203] usb 1-2: device descriptor read/8, error -62
[175119.399199] usb 1-2: device descriptor read/8, error -62
[175119.500031] hub 1-0:1.0: unable to enumerate USB device on port 2
[175283.956031] usb 1-2: new full speed USB device using ohci_hcd and address 13
[175284.159274] usb 1-2: device descriptor read/all, error -62
[175284.337022] usb 1-2: new full speed USB device using ohci_hcd and address 14
[175284.521034] usb 1-2: device descriptor read/64, error -62
[175284.805046] usb 1-2: device descriptor read/64, error -62
[175285.084044] usb 1-2: new full speed USB device using ohci_hcd and address 15
[175285.493025] usb 1-2: device not accepting address 15, error -62
[175285.669046] usb 1-2: new full speed USB device using ohci_hcd and address 16
[175285.699272] usb 1-2: device descriptor read/8, error -62
[175285.824271] usb 1-2: device descriptor read/8, error -62
[175285.929260] hub 1-0:1.0: unable to enumerate USB device on port 2
[175328.952029] usb 1-2: new full speed USB device using ohci_hcd and address 17
[175329.155291] usb 1-2: device descriptor read/all, error -62
[175329.332027] usb 1-2: new full speed USB device using ohci_hcd and address 18
[175329.535289] usb 1-2: device descriptor read/all, error -62
[175329.712029] usb 1-2: new full speed USB device using ohci_hcd and address 19
[175329.739290] usb 1-2: device descriptor read/8, error -62
[175329.863288] usb 1-2: device descriptor read/8, error -62
[175330.140026] usb 1-2: new full speed USB device using ohci_hcd and address 20
[175330.167289] usb 1-2: device descriptor read/8, error -62
[175330.292293] usb 1-2: device descriptor read/8, error -62
[175330.397026] hub 1-0:1.0: unable to enumerate USB device on port 2
[176713.788026] usb 1-2: new full speed USB device using ohci_hcd and address 21
[176714.372370] usb 1-2: device not accepting address 21, error -62
[176714.548036] usb 1-2: new full speed USB device using ohci_hcd and address 22
[176714.728029] usb 1-2: device descriptor read/64, error -62
[176715.035856] usb 1-2: device descriptor read/all, error -62
[176715.212046] usb 1-2: new full speed USB device using ohci_hcd and address 23
[176715.239859] usb 1-2: device descriptor read/8, error -62
[176715.363854] usb 1-2: device descriptor read/8, error -62
[176715.640048] usb 1-2: new full speed USB device using ohci_hcd and address 24
[176715.667853] usb 1-2: device descriptor read/8, error -62
[176715.791854] usb 1-2: device descriptor read/8, error -62
[176715.892028] hub 1-0:1.0: unable to enumerate USB device on port 2




If I type uname -a I got:

> Linux ubuntu 2.6.27-11-generic #1 SMP Wed Apr 1 20:53:41 UTC 2009 x86_64 GNU/Linux

---

### Post by znuxor on 2011-02-12
I got the same problem

Here is what happens when I plug it.
dmesg:
> [  339.744112] usb 5-1: new full speed USB device using ohci_hcd and address 3
[  339.884100] usb 5-1: device descriptor read/64, error -62
[  340.128090] usb 5-1: device descriptor read/64, error -62
[  340.368101] usb 5-1: new full speed USB device using ohci_hcd and address 4
[  340.528623] usb 5-1: device descriptor read/all, error -62
[  340.668095] usb 5-1: new full speed USB device using ohci_hcd and address 5
[  340.692699] usb 5-1: device descriptor read/8, error -62
[  340.816752] usb 5-1: device descriptor read/8, error -62
[  341.056091] usb 5-1: new full speed USB device using ohci_hcd and address 6
[  341.080873] usb 5-1: device descriptor read/8, error -62
[  341.204929] usb 5-1: device descriptor read/8, error -62
[  341.308149] hub 5-0:1.0: unable to enumerate USB device on port 1

Error 62 from /usr/include/asm-generic/errno.h:
> #define ETIME           62      /* Timer expired */


> $ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 0bda:8189 Realtek Semiconductor Corp. RTL8187B Wireless 802.11g 54Mbps Network Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

The usb hub is not detected by lsusb.

> :~$ uname -a
Linux znuxor-desktop 2.6.35-25-generic-pae #44-Ubuntu SMP Fri Jan 21 19:01:46 UTC 2011 i686 GNU/Linux

This is happening on all of my usb ports. The hub is working on my netbook, so it isn't broken. It also seems to happen with portable devices(ipod) if they are not in disk mode.:(

My motherboard is a MSI 880gma-e45.

---

