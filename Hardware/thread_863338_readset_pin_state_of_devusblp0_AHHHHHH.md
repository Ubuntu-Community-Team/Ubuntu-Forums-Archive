---
title: "read/set pin state of /dev/usblp0? AHHHHHH"
date: 2008-07-18
forum: Hardware
---

### Post by swharden on 2008-07-18
I have a USB printer port (36 pin) adapter. I want to directly control the state of the pins.  **I have a volt meter attached to pin 2 (data0) and pin 19 (ground) and it reads ~5v.  If I "cat /dev/urandom > /dev/usblp0", voltage drops to 0v. I can't seem to get it to go back up to 5v again.  I have to unplug the USB and re-plug it, then it's back to normal (5v).  How do I determine which data pins are on and which are off?!?**

The traditional way to set pins of a printer port is to act on /dev/port modifying data at the base address (ex: 0x378 ).  I'd love to do this, but I can't figure out what the base address is (if there is one).  My /proc/ioports is at the bottom.  My hunch was that it was 0xaf40, but I've tried setting the data for all the 0xafxx's and it doesn't seem to do anything at all.  (Is 0xaf40 the io address of the usb controller? - does a virtual port even HAVE an io address??)

```

contents of /proc/ioports:

0000-001f : dma1
0020-0021 : pic1
0040-0043 : timer0
004e-004f : tpm_infineon0
0050-0053 : timer1
0060-006f : keyboard
0070-0077 : rtc
0080-008f : dma page reg
00a0-00a1 : pic2
00c0-00df : dma2
00f0-00ff : fpu
0170-0177 : 0000:00:1f.2
  0170-0177 : libata
01e0-01ef : pnp 00:09
01f0-01f7 : 0000:00:1f.2
  01f0-01f7 : libata
0376-0376 : 0000:00:1f.2
  0376-0376 : libata
03c0-03df : vga+
03f6-03f6 : 0000:00:1f.2
  03f6-03f6 : libata
0680-068f : tpm_infineon0
0cf8-0cff : PCI conf1
1000-1fff : PCI Bus #03
  1000-10ff : PCI CardBus #04
  1400-14ff : PCI CardBus #04
af10-af1f : 0000:00:1f.2
  af10-af1f : libata
af40-af5f : 0000:00:1d.3
  af40-af5f : uhci_hcd
af60-af7f : 0000:00:1d.2
  af60-af7f : uhci_hcd
af80-af9f : 0000:00:1d.1
  af80-af9f : uhci_hcd
afe0-afff : 0000:00:1d.0
  afe0-afff : uhci_hcd
b000-bfff : PCI Bus #01
  bfe0-bfff : 0000:01:00.0
    bfe0-bfff : e1000
cff8-cfff : 0000:00:02.0
d800-d87f : 0000:00:1f.0
  d800-d803 : ACPI PM1a_EVT_BLK
  d804-d805 : ACPI PM1a_CNT_BLK
  d808-d80b : ACPI PM_TMR
  d810-d815 : ACPI CPU throttle
  d820-d820 : ACPI PM2_CNT_BLK
  d828-d82f : ACPI GPE0_BLK
  d860-d87f : iTCO_wdt
eec0-eeff : 0000:00:1f.0

```

---

### Post by foffop on 2009-04-14
I have exactly the same problem.
It seem we have to enable the uss720 kernel module with which /dev/usblp0 is displayed as /dev/parport1. But I don't understand in what way the kernel has to be recompiled, because in Linux 2.6.27-11-generic uss720 is configured as a module...

[http://www.linux-usb.org/USB-guide/x532.html](http://www.linux-usb.org/USB-guide/x532.html)

---

