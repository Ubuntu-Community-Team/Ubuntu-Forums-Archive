---
title: "USB ports not working on 9.04"
date: 2009-07-19
forum: Hardware
---

### Post by naomibrown on 2009-07-19
Hi,

I'm working on a Toshiba Tecra and I can't get my USB ports to work. I'm trying to plug a USB stick into them, but it isn't there in Computer and it doesn't mount. 

I've tried all the different USB ports and I've tried using a cardbus too, but no-one could help me get this working ([http://swiss.ubuntuforums.org/showthread.php?t=1210481]("http://swiss.ubuntuforums.org/showthread.php?t=1210481"))

I've tried using lots of different options for booting with the "noapic" option from ([http://ubuntuforums.org/showthread.php?t=148761]("http://ubuntuforums.org/showthread.php?t=148761")).

lspci said:
00:00.0 Host bridge: Intel Corporation 82830 830 Chipset Host Bridge (rev 02)
00:01.0 PCI bridge: Intel Corporation 82830 830 Chipset AGP Bridge (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801CA/CAM USB Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801CA/CAM USB Controller #3 (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 41)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 01)
01:00.0 VGA compatible controller: S3 Inc. SuperSavage IX/C SDR (rev 05)
02:07.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
02:08.0 Ethernet controller: Intel Corporation 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller (rev 41)
02:0a.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 01)
02:0b.0 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 32)
02:0b.1 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 32)
02:0d.0 System peripheral: Toshiba America Info Systems SD TypA Controller (rev 03)
09:00.0 USB Controller: NEC Corporation USB (rev 43)
09:00.1 USB Controller: NEC Corporation USB (rev 43)
09:00.2 USB Controller: NEC Corporation USB 2.0 (rev 04)

And lsusb said:
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Please help! I don't know what else to try.

---

### Post by naomibrown on 2009-07-19
I've just read a couple of other posts - 

When I boot with the USB drive in I get:

naomi@ubuntu:~$ lsusb
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
naomi@ubuntu:~$ 
naomi@ubuntu:~$ blkid
/dev/sda1: UUID="197e5331-d03a-4684-aa0b-d3c9f9345028" TYPE="ext3" 
/dev/sda5: UUID="b166be5f-b746-4317-8c1f-5ac8d4d337b8" TYPE="swap" 

When I boot without the USB drive in I get:

naomi@ubuntu:~$ lsusb
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
naomi@ubuntu:~$ 
naomi@ubuntu:~$ blkid
/dev/sda1: UUID="197e5331-d03a-4684-aa0b-d3c9f9345028" TYPE="ext3" 
/dev/sda5: UUID="b166be5f-b746-4317-8c1f-5ac8d4d337b8" TYPE="swap"

I also tried:

sudo mkdir /media/USB
sudo mount /dev/sdb1 /media/USB

but it said:
mount: special device /dev/sdb1 does not exist

:(

---

### Post by Xerada on 2009-07-19
Hello naomibrown, 

I had a similar problem (after updating) and found I hadn't installed the proper software any more. So, maybe try out ```
sudo apt-get pmount
``` and restart - it solved my problem. ```
pmount
``` allows non-root users to (auto)mount removable usb drives. 

Greetings, 
Xerada

---

### Post by naomibrown on 2009-07-20
Thanks Xerada!

> **Xerada said:**
> ```
sudo apt-get pmount
``` and restart - it solved my problem.

This didn't work, but then I figured you meant ```
 sudo apt-get install pmount
```. That installed fine but it still doesn't work after a reboot.

I've tried rebooting a couple of times.

Any other ideas anyone?

---

### Post by naomibrown on 2009-07-20
I've also tried:

```

naomi@ubuntu:~$ sudo update-pciids; lspci | grep USB
[sudo] password for naomi: 
00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801CA/CAM USB Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801CA/CAM USB Controller #3 (rev 01)
09:00.0 USB Controller: NEC Corporation USB (rev 43)
09:00.1 USB Controller: NEC Corporation USB (rev 43)
09:00.2 USB Controller: NEC Corporation USB 2.0 (rev 04)

```

The download failed when I tried:
```

naomi@ubuntu:~$ sudo update-usbids; lsusb
--2009-07-20 18:57:41--  http://linux-usb.sourceforge.net/usb.ids
Resolving linux-usb.sourceforge.net... failed: Name or service not known.
wget: unable to resolve host address `linux-usb.sourceforge.net'
update-usbids: download failed
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

```

naomi@ubuntu:~$ lsmod | grep usb
usb_storage            99520  0 

```

still no joy :(

---

### Post by naomibrown on 2009-07-21
How can I get the download to work properly? Other people seem to have got this to work using the same commands...

---

