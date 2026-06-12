---
title: "Setting up US Robotic Wireless adapter"
date: 2007-02-24
forum: Hardware &amp; Laptops
---

### Post by shadyzay on 2007-02-24
hi everybody,
I'm trying to set up a USR-5411 wireless card on a compaq nx9010 laptop ( running edgy),
I installed ndiswrapper, grabbed the latest compatible drivers ( as listed [here]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/List") ), installed it ```
ndiswrapper -i drivername.inf
``` and checked it with ```
ndiswrapper -l
```,  performed a modprobe, everything looks as suggessted by the wiki.
When trying to enable the interface in systemsettings, it displays the green check mark for less than a second then goes back to disabled without any error messages.
Trying to ifup the interface gives this output:
```
oem@(none):~/tmp3$ sudo ifup eth1
SIOCSIFFLAGS: No such file or directory
SIOCSIFFLAGS: No such file or directory
Failed to bring up eth1.
```
I checked the system messages:
```
Feb 24 17:28:08 (none) kernel: [17179975.200000] ndiswrapper version 1.37 loaded (preempt=no,smp=yes)
Feb 24 17:28:08 (none) kernel: [17179975.240000] usbcore: registered new driver ndiswrapper
Feb 24 17:30:42 (none) kernel: [17180129.728000] pccard: card ejected from slot 0
Feb 24 17:30:43 (none) kernel: [17180129.804000] ACPI: PCI interrupt for device 0000:02:00.0 disabled
Feb 24 17:31:15 (none) kernel: [17180162.228000] pccard: CardBus card inserted into slot 0
Feb 24 17:31:15 (none) kernel: [17180162.228000] PCI: Enabling device 0000:02:00.0 (0000 -> 0002)
Feb 24 17:31:15 (none) kernel: [17180162.228000] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [LNK5] -> GSI 11 (level, low) -> IRQ 11
```

I also tried extracting the drivers from the windows installation provided with the card, replayed all the steps, but nothing has changed.

Can any body help in this?

---

### Post by tomiu on 2007-05-16
did u find any solution?? if YES plss tell me too.

---

