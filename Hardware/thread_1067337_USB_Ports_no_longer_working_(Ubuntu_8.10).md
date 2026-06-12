---
title: "USB Ports no longer working (Ubuntu 8.10)"
date: 2009-02-11
forum: Hardware
---

### Post by vital101 on 2009-02-11
Hey everyone,

I just recently noticed that the USB ports on my laptop have stopped working.  I don't think that it's a problem with hardware.  Is there anyway I can re-activate them, figure out what is wrong with them, etc?

Thanks,
vital101

---

### Post by ajmorris on 2009-02-13
> **vital101 said:**
> Hey everyone,

I just recently noticed that the USB ports on my laptop have stopped working.  I don't think that it's a problem with hardware.  Is there anyway I can re-activate them, figure out what is wrong with them, etc?

Thanks,
vital101

hi there,
just to make sure that your computer is still giving power to the ports, can you post the output of:
```
sudo lspci
```
and:
```
sudo lsusb
```

If so, either your HAL has gone on the frits, or your usb kernel drivers are acting up. Once we know for certain that they still have power, we can go about debugging the problem :)

AJ

---

### Post by darramonde on 2009-03-02
> **ajmorris said:**
> hi there,
just to make sure that your computer is still giving power to the ports, can you post the output of:
```
sudo lspci
```
and:
```
sudo lsusb
```

If so, either your HAL has gone on the frits, or your usb kernel drivers are acting up. Once we know for certain that they still have power, we can go about debugging the problem :)

AJ

I tried the above mentioned with the following results:

(sudo lspci)

00:00.0 Host bridge: VIA Technologies, Inc. CN333/CN400/PM880 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. CN333/CN400/PM880 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. CN333/CN400/PM880 CPU Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. CN333/CN400/PM880 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. CN333/CN400/PM880 Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. CN333/CN400/PM880 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
00:06.0 Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
01:00.0 VGA compatible controller: VIA Technologies, Inc. CN400/PM800/PM880/PN800/PN880 [S3 UniChrome Pro] (rev 02)
 
(sudo lsusb)

 
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

What to do?

---

