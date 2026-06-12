---
title: "nforce irq problem"
date: 2006-07-18
forum: Hardware &amp; Laptops
---

### Post by ctaggart on 2006-07-18
Dapper is freezing on me quite frequently.  I've been troubleshooting it for a few days now and I think it might be an irq problem.

Some background info I posted in "Dapper freezes 1-3 times a day"
[http://ubuntuforums.org/showthread.php?p=1261086#post1261086](http://ubuntuforums.org/showthread.php?p=1261086#post1261086)

I have Asus A7N266-E motherboard with a nVidia nForce 420-D chipset (nForce 1).  Any help troubleshooting this would be great!  Not sure if any of this will help:

ctaggart@ubuntu:~$ cat /proc/interrupts
           CPU0
  0:     682087    IO-APIC-edge  timer
  1:       1313    IO-APIC-edge  i8042
  8:          4    IO-APIC-edge  rtc
  9:          0   IO-APIC-level  acpi
 14:      11000    IO-APIC-edge  ide0
 15:      47692    IO-APIC-edge  ide1
177:      59002   IO-APIC-level  ohci_hcd:usb1, ohci_hcd:usb2
185:        141   IO-APIC-level  NVidia nForce
201:     783434   IO-APIC-level  ath0
NMI:          0
LOC:     677523
ERR:          0
MIS:          0

ctaggart@ubuntu:~$ cat /var/log/messages | grep irq
...
Jul 18 07:43:17 localhost kernel: [17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl edge)
Jul 18 07:43:17 localhost kernel: [17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Jul 18 07:43:17 localhost kernel: [17179570.432000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Jul 18 07:43:17 localhost kernel: [17179570.820000] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
Jul 18 07:43:17 localhost kernel: [17179570.820000] PNP: PS/2 controller doesn't have AUX irq; using default 12
Jul 18 07:43:17 localhost kernel: [17179570.820000] serio: i8042 AUX port at 0x60,0x64 irq 12
Jul 18 07:43:17 localhost kernel: [17179570.820000] serio: i8042 KBD port at 0x60,0x64 irq 1
Jul 18 07:43:17 localhost kernel: [17179573.244000] NFORCE: not 100%% native mode: will probe irqs later
Jul 18 07:43:17 localhost kernel: [17179574.204000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
Jul 18 07:43:17 localhost kernel: [17179575.296000] ide1 at 0x170-0x177,0x376 on irq 15
Jul 18 07:43:17 localhost kernel: [17179576.024000] ohci_hcd 0000:00:02.0: irq 177, io mem 0xef000000
Jul 18 07:43:17 localhost kernel: [17179576.184000] ohci_hcd 0000:00:03.0: irq 177, io mem 0xee800000
Jul 18 07:43:17 localhost kernel: [17179590.532000] ath0: Atheros 5212: mem=0xec800000, irq=201

---

### Post by ctaggart on 2006-07-25
One of my Mushkin RAM modules went bad after 4 years of use.  It is looking like that might be the root cause.

---

