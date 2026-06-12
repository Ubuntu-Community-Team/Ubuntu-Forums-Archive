---
title: "Embedded sound chip not recognized, 12.10 Need help"
date: 2012-12-14
forum: Hardware
---

### Post by PaperPilot on 2012-12-14
Ubuntu does not find my motherboard's sound chip.  It is an ATI SBx00 Azalia chip on a Gigabyte GA-78LMT-S2P board.

The command hwinfo --sound output:

> 19: PCI 14.2: 0403 Audio device                                 
  [Created at pci.318]
  Unique ID: 5Dex.9zCmC9gVD38
  SysFS ID: /devices/pci0000:00/0000:00:14.2
  SysFS BusID: 0000:00:14.2
  Hardware Class: sound
  Model: "ATI SBx00 Azalia (Intel HDA)"
  Vendor: pci 0x1002 "ATI Technologies Inc"
  Device: pci 0x4383 "SBx00 Azalia (Intel HDA)"
  SubVendor: pci 0x1458 "Giga-byte Technology"
  SubDevice: pci 0xa002 
  Memory Range: 0xfe024000-0xfe027fff (rw,non-prefetchable)
  IRQ: 7 (no events)
  Module Alias: "pci:v00001002d00004383sv00001458sd0000A002bc04sc03i00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown



Here is the system page:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=228674&stc=1&d=1355519920[/IMG]

I have not been able to find a driver, but I think the first step is to get the machine to recognize the chip.

Can anybody help?

---

### Post by TheFu on 2012-12-14
[https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure) might be helpful.

---

### Post by PaperPilot on 2012-12-16
After much searching and trial, I have determined the the problem rests with the 3.5.0-19-generic kernel.  When I droop back to the 3.5.0-18-generic, the computer finds all audio hardware and selects the proper snd driver.

I tried to report this bug on launchpad, but when I clicked on the "Report a bug" link I was sent to the bug report etiquette page.  I will have to hope this problem has been reported and will be resolved with release 3.5.0-120-generic.

---

### Post by PaperPilot on 2012-12-19
Upgrade to the newly released -21 kernel solved the problem.  Sounds great now.

---

