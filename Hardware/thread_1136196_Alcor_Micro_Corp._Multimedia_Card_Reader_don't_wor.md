---
title: "Alcor Micro Corp. Multimedia Card Reader don't work after upgrading Ubuntu to 9.04"
date: 2009-04-24
forum: Hardware
---

### Post by Leolik on 2009-04-24
In 8.10 cardreader work fine. After update - not work.
In lsusb - it displayed:
Bus 001 Device 005: ID 058f:6377 Alcor Micro Corp. Multimedia Card Reader
but in system - not displayed.
I try insert memory card to cardreader - nothing happened.
In dmesg and other logs nothing displayed :(
Any ideas?

Ubuntu 9.04 amd64

---

### Post by ninboy on 2009-04-25
Mine lsusb shows:```
Bus 001 Device 003: ID 0bda:0158 Realtek Semiconductor Corp. Mass Stroage Device
```. Same here, it worked in 8.10, but it doesn't work in 9.04

---

### Post by upptown on 2009-05-08
Here is the out put of "lsusb"

```
Bus 001 Device 013: ID 058f:6366 Alcor Micro Corp. 
Bus 001 Device 008: ID 058f:6362 Alcor Micro Corp. Hi-Speed 21-in-1 Flash Card Reader/Writer (Internal/External)
Bus 001 Device 003: ID 059b:0277 Iomega Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

Added ```
usb_modules
``` to /etc/modules 

That got device 008 (058f:6362 Alcor Micro Corp) working.
But no joy on Device 013 (058f:6366 Alcor Micro Corp).  

Device 013 connects to a USB riser on the mobo.  
Device 008 is a generic $19 USB card reader.

From what I've read this issue could be related to the ehci_hcd module and about the only fix is to disable ehci_module which means you won't have USB 2.0 support on your system.  Does anyone have an alternate fix that doesn't kill USB 2.0?

---

### Post by hops-1 on 2009-06-17
It seems taht I have a similar problem with my card reader. It is an Alcor card reader as above and my lsusb output reads as follows:

```

>:~$ lsusb
Bus 001 Device 006: ID 058f:6362 Alcor Micro Corp. Hi-Speed 21-in-1 Flash Card Reader/Writer (Internal/External)
Bus 001 Device 002: ID 045e:074a Microsoft Corp.
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 046a:0023 Cherry GmbH Cymotion Master Linux Keyboard
Bus 004 Device 002: ID 046d:c506 Logitech, Inc. MX-700 Cordless Mouse Receiver
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

I added ```
usb_modules
``` to ```
/etc/modules
```, but it stilldoes not work.

Is there any other idea to get the device to work. It worked just fine with Ubuntu 8.10 and before...

---

### Post by Digicrat on 2009-09-20
Did either of you ever manage to get that card working?  Not to hijack an old thread, but I'm having a similar problem now with a new internal USB MMC reader that I've just installed.  

The device is being detected, but I can't mount it (manually or automatically).  It doesn't appear to detect anything when I insert or remove a card, though if a card is connected on boot it does appear to find the SD card and fails to read capacity. The reader also has an extra USB port on it that I tested out of curiosity, and it appears that port isn't working either.

Any ideas? Or am I going to be making another trip to MicroCenter next week ...


lsusb shows my reader as: 
```
Bus 002 Device 005: ID 058f:6377 Alcor Micro Corp. Multimedia Card Reader
```


dmesg includes:
```

[  109.550428] scsi 10:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
[  109.551292] scsi 10:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
[  109.552167] scsi 10:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ: 0 ANSI: 0
[  109.553044] scsi 10:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0
[  109.554038] scsi 10:0:0:4: Direct-Access     Generic  Mini SD Reader   1.06 PQ: 0 ANSI: 0
[  139.664022] usb 2-5: reset high speed USB device using ehci_hcd and address 5
[  149.908519] usb 2-5: reset high speed USB device using ehci_hcd and address 5
[  166.152519] usb 2-5: reset high speed USB device using ehci_hcd and address 5
[  166.400023] usb 2-5: reset high speed USB device using ehci_hcd and address 5
[  176.644021] usb 2-5: reset high speed USB device using ehci_hcd and address 5
[  176.778803] sd 10:0:0:0: Device offlined - not ready after error recovery
[  176.778848] sd 10:0:0:0: rejecting I/O to offline device
[  176.778857] sd 10:0:0:0: rejecting I/O to offline device
[  176.778862] sd 10:0:0:0: rejecting I/O to offline device
[  176.778866] sd 10:0:0:0: [sdc] READ CAPACITY failed
[  176.778867] sd 10:0:0:0: [sdc] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[  176.778871] sd 10:0:0:0: [sdc] Sense not available.
[  176.778875] sd 10:0:0:0: rejecting I/O to offline device
[  176.778879] sd 10:0:0:0: [sdc] Write Protect is off
[  176.778881] sd 10:0:0:0: [sdc] Mode Sense: 00 00 00 00
[  176.778882] sd 10:0:0:0: [sdc] Assuming drive cache: write through
[  176.778985] sd 10:0:0:0: [sdc] Attached SCSI removable disk
[  176.779096] sd 10:0:0:0: Attached scsi generic sg3 type 0
[  176.783299] sd 10:0:0:1: [sdd] Attached SCSI removable disk
[  176.783703] sd 10:0:0:1: Attached scsi generic sg4 type 0
[  176.785540] sd 10:0:0:2: [sde] Attached SCSI removable disk
[  176.785892] sd 10:0:0:2: Attached scsi generic sg5 type 0
[  176.790290] sd 10:0:0:3: [sdf] Attached SCSI removable disk
[  176.790649] sd 10:0:0:3: Attached scsi generic sg6 type 0
[  176.795827] sd 10:0:0:4: [sdg] Attached SCSI removable disk
[  176.796254] sd 10:0:0:4: Attached scsi generic sg7 type 0
```

---

### Post by TheHardDisk on 2009-10-17
I can confirm this issue as well.  Light turns green when a memory card is inserted.  Then nothing, I know it is detected fine and works since I can use it when i enable usb support for it in Virtualbox with Windows XP as a guest.

lsusb:

```
Bus 002 Device 002: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
```


dmesg:
```
[ 1171.492387] warning: `VirtualBox' uses 32-bit capabilities (legacy support in use)
[ 1181.172290] usb 2-1: reset full speed USB device using ohci_hcd and address 2
[ 1191.560328] usb 2-1: reset full speed USB device using ohci_hcd and address 2
[ 1207.972029] usb 2-1: reset full speed USB device using ohci_hcd and address 2
[ 1208.360108] usb 2-1: reset full speed USB device using ohci_hcd and address 2
[ 1218.740036] usb 2-1: reset full speed USB device using ohci_hcd and address 2
[ 1218.946971] sd 6:0:0:0: Device offlined - not ready after error recovery
[ 1831.013226] udev: starting version 147
[ 1902.212042] usb 1-2: new high speed USB device using ehci_hcd and address 6
[ 1902.355644] usb 1-2: configuration #1 chosen from 1 choice
[ 1902.356574] scsi8 : SCSI emulation for USB Mass Storage devices
[ 1902.357339] usb-storage: device found at 6
[ 1902.357342] usb-storage: waiting for device to settle before scanning
[ 1907.364200] usb-storage: device scan complete
```

---

### Post by darsu on 2009-12-06
I have something similar here. I just bought a Delock 34-in-1 internal card reader which was advertised as kernel 2.6* compatible. It shows up in lsusb as

```

Bus 005 Device 003: ID 058f:6361 Alcor Micro Corp.

```

so chances are it's got some of the same innards.

I've tested the reader with SDHC cards and USB devices. SDHC cards do work although I have to find out which /dev/sd** it shows up as in order to be able to mount it, which is a bit of a nuisance (I'm not using Gnome, KDE or such integrated desktop environments which, I gather, may do such things automatically). The USB port, alas, shows no sign of functioning, and I'm wondering if it's a defective item or if there's something I'm doing wrong. 

Inserting things in the reader's various slots doesn't cause any dmesg output. 


Any insight?

---

### Post by weidongche on 2009-12-19
same problem here, please someone fix it.

---

### Post by dibblego on 2010-01-02
Bump.

---

### Post by dibblego on 2010-01-03
Buuuuump!

Did any of you guys figure anything out?

---

### Post by draco31.fr on 2010-01-10
That is a problem with the ehci_hcd module.
You can see the following bug reports :
[https://bugs.launchpad.net/ubuntu/+bug/366478](https://bugs.launchpad.net/ubuntu/+bug/366478)
[https://bugs.launchpad.net/ubuntu/+bug/88746](https://bugs.launchpad.net/ubuntu/+bug/88746)

If you aren't on Karmic, you can unload the ehci_hcd module and try again :
sudo modprobe -r ehci_hcd

If you use Karmic, you cann't unload the module, but you can use the command line in those bug report :
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/354832](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/354832)

---

### Post by vashman on 2010-02-16
I have the kind of same reader and mine has worked fine since dapper.
 ```
Bus 001 Device 002: ID 045e:0728 Microsoft Corp.
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```
 though i've only used the reader to read usb drives and SD cards.
I've used a set of SanDisk cards and many different types of usb devices. All devices have worked great except when trying to safly remove the card; at which point the device will turn off and remain off.
Also my reader does not support SDHC types.

---

### Post by draco31.fr on 2010-02-16
The mine is running fine on Karmic 64 bits (it doesn't on Jaunty) :

> Bus 001 Device 013: ID 058f:6366 Alcor Micro Corp. Multi Flash Reader
Bus 001 Device 012: ID 058f:6254 Alcor Micro Corp. USB Hubdmesg :
> [1225277.650865] usb 1-1.3: new high speed USB device using ehci_hcd and address 12
[1225277.761868] usb 1-1.3: configuration #1 chosen from 1 choice
[1225277.762160] hub 1-1.3:1.0: USB hub found
[1225277.762384] hub 1-1.3:1.0: 4 ports detected
[1225278.060266] usb 1-1.3.4: new high speed USB device using ehci_hcd and address 13
[1225278.172269] usb 1-1.3.4: configuration #1 chosen from 1 choice
[1225278.172753] scsi16 : SCSI emulation for USB Mass Storage devices
[1225278.172999] usb-storage: device found at 13
[1225278.173003] usb-storage: waiting for device to settle before scanning
[1225283.159256] usb-storage: device scan complete
[1225283.160238] scsi 16:0:0:0: Direct-Access     Multi    Flash Reader     1.00 PQ: 0 ANSI: 0
[1225283.162007] sd 16:0:0:0: Attached scsi generic sg11 type 0
[1225283.166315] sd 16:0:0:0: [sdg] Attached SCSI removable disk

I also changed my motherboard, so maybe the USB Controler was guilty.

---

### Post by Lampi on 2010-04-21
Here's what I figured out: my usb reader turned out to be an outdated piece of hardware for SD capacities >2GB 

Try it yourself with an older sd card < 2gb - it could be working.

The 4GB SD card I was trying to use only works with a new inbuilt card reader on my laptop I recently bought.

---

### Post by megabyte1234 on 2010-09-04
I have also an Alcor Micro Corp. 8-in-1 Media Card Reader says lsusb, and on Ubuntu 10.04 it also doesn't work...

---

### Post by dr.micro on 2011-12-25
Transcend microSDHC 16GB + retail usb reader (ID 058f:6366 Alcor Micro Corp. Multi Flash Reader) don't work in Ubuntu 10.04LTS

---

