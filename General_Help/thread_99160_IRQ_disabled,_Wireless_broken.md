---
title: "IRQ disabled, Wireless broken"
date: 2005-12-05
forum: General Help
---

### Post by bananana on 2005-12-05
My wireless was working fine until I started trying to get my usb flash reader working. After I realized I'd broken my wireless, I tried to undo everything I did, but I can't get it back.

I had to use the kernel parameters "acpi=noirq apm=off" in order to get my wireless working in the first place. They're still there, but now I get this when I'm booting up:

[FONT="Fixedsys"]
[4294710.288000] IRQ routing conflict for 0000:01:05.0, have irq 10, want irq 11
[4294710.345000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[10]  MMIO=[d000c000-d000c7ff]  Max Packet=[2048]
[4294710.756000] irq 10: nobody cared (try booting with the "irqpoll" option.
[4294710.756000]  [<c012df63>] __report_bad_irq+0x31/0x74
[4294710.756000]  [<c012e03b>] note_interrupt+0x7d/0xa2
[4294710.756000]  [<c012db60>] __do_IRQ+0x85/0xb1
[4294710.756000]  [<c0104ca5>] do_IRQ+0x19/0x24
[4294710.756000]  [<c01038b6>] common_interrupt+0x1a/0x20
[4294710.756000] handlers:
[4294710.756000] [<dcb66177>] (ohci_irq_handler+0x0/0x587 [ohci1394])
[4294710.756000] Disabling IRQ #10
[/FONT]

IRQ #10 is what my wireless uses:

[FONT="Fixedsys"]
# cat /proc/interrupts
           CPU0
  0:     868697          XT-PIC  timer
  1:       2541          XT-PIC  i8042
  2:          0          XT-PIC  cascade
  8:          1          XT-PIC  rtc
  9:        123          XT-PIC  acpi
 10:     100002          XT-PIC  ohci1394, ndiswrapper, radeon@pci:0000:01:05.0
 11:       2181          XT-PIC  ohci_hcd:usb1, ohci_hcd:usb2, ehci_hcd:usb3, ALI 5451, eth0
 12:      28935          XT-PIC  i8042
 14:      10076          XT-PIC  ide0
 15:       6277          XT-PIC  ide1
NMI:          0
LOC:          0
ERR:          0
MIS:          0
[/FONT]

I tried using the "irqpoll" parameter, but it didn't help. Any ideas?

---

### Post by bananana on 2005-12-05
A decent temporary fix might be to remove the conflicting firewire module. In gentoo, there is a directory /etc/modules.autoload.d/ that controls which kernel modules are loaded at bootup. I couldn't find the ubuntu equivalent. /etc/modules looked promising, but ohci1394 wasn't there to remove. Is there any way other than deleting the module to prevent it from being loaded automatically?

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
mousedev
psmouse
sbp2
sr_mod

---

