---
title: "IRQ problems on thinkpad a21p"
date: 2004-10-25
forum: Hardware &amp; Laptops
---

### Post by voyaman on 2004-10-25
hi i have the next problem:

when i run ubuntu first time, on dmesg appear an FATAL error when try to load pci_hotplug:

pci_hotplug: PCI Hot Plug PCI Core version: 0.5
pciehp: acpi_pciehprm:\_SB_.PCI0 evaluate _BBN fail=0x5
pciehp: acpi_pciehprm:get_device PCI ROOT HID fail=0x5
shpchp: acpi_shpchprm:\_SB_.PCI0 evaluate _BBN fail=0x5
shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x5

but it pass, and i have no more problem to login on gnome, but when i close the session to in with another user, recieve the next error on dmesg:

irq 9: nobody cared!
 [<c0108006>] __report_bad_irq+0x2a/0x8b
 [<c01080f0>] note_interrupt+0x6f/0x9f
 [<c01083b2>] do_IRQ+0x127/0x136
 [<c0106834>] common_interrupt+0x18/0x20
 [<c011f7b3>] __do_softirq+0x2f/0x80
 [<c011f82a>] do_softirq+0x26/0x28
 [<c010838e>] do_IRQ+0x103/0x136
 [<c0106834>] common_interrupt+0x18/0x20
handlers:
[<c01aac9b>] (acpi_irq+0x0/0x16)
[<d09f47f3>] (yenta_interrupt+0x0/0x39 [yenta_socket])
[<d0ab979c>] (snd_cs46xx_interrupt+0x0/0x1fa [snd_cs46xx])
Disabling IRQ #9

then the sound crash, and if i want to restart the computer, it fails to load another time and said Kernel Panic : error with the sound card and irq, then i need to turn off the computer and turn on to fix.
while i don't close the first gnome session doesn't pass anything.
the problem is when close the gnome session and go to gdm.

my laptop is IBM Thinkpad a21p
my lspci is:
0000:00:00.0 Host bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
0000:00:01.0 PCI bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
0000:00:02.0 CardBus bridge: Texas Instruments PCI1450 (rev 03)
0000:00:02.1 CardBus bridge: Texas Instruments PCI1450 (rev 03)
0000:00:03.0 Ethernet controller: Intel Corp. 82557/8/9 [Ethernet Pro 100] (rev 09)
0000:00:03.1 Serial controller: Xircom Mini-PCI V.90 56k Modem
0000:00:05.0 Multimedia audio controller: Cirrus Logic CS 4614/22/24 [CrystalClear SoundFusion Audio Accelerator] (rev 01)
0000:00:07.0 Bridge: Intel Corp. 82371AB/EB/MB PIIX4 ISA (rev 02)
0000:00:07.1 IDE interface: Intel Corp. 82371AB/EB/MB PIIX4 IDE (rev 01)
0000:00:07.2 USB Controller: Intel Corp. 82371AB/EB/MB PIIX4 USB (rev 01)
0000:00:07.3 Bridge: Intel Corp. 82371AB/EB/MB PIIX4 ACPI (rev 03)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Rage Mobility M3 AGP 2x (rev 02)


please help me.

---

### Post by UberGeek on 2004-10-25
[QUOTE=voyaman]hi i have the next problem:

when i run ubuntu first time, on dmesg appear an FATAL error when try to load pci_hotplug:

pci_hotplug: PCI Hot Plug PCI Core version: 0.5
pciehp: acpi_pciehprm:\_SB_.PCI0 evaluate _BBN fail=0x5
pciehp: acpi_pciehprm:get_device PCI ROOT HID fail=0x5
shpchp: acpi_shpchprm:\_SB_.PCI0 evaluate _BBN fail=0x5
shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x5

but it pass, and i have no more problem to login on gnome, but when i close the session to in with another user, recieve the next error on dmesg:

irq 9: nobody cared!
 [<c0108006>] __report_bad_irq+0x2a/0x8b
 [<c01080f0>] note_interrupt+0x6f/0x9f
 [<c01083b2>] do_IRQ+0x127/0x136
 [<c0106834>] common_interrupt+0x18/0x20
 [<c011f7b3>] __do_softirq+0x2f/0x80
 [<c011f82a>] do_softirq+0x26/0x28
 [<c010838e>] do_IRQ+0x103/0x136
 [<c0106834>] common_interrupt+0x18/0x20
handlers:
[<c01aac9b>] (acpi_irq+0x0/0x16)
[<d09f47f3>] (yenta_interrupt+0x0/0x39 [yenta_socket])
[<d0ab979c>] (snd_cs46xx_interrupt+0x0/0x1fa [snd_cs46xx])
Disabling IRQ #9

then the sound crash, and if i want to restart the computer, it fails to load another time and said Kernel Panic : error with the sound card and irq, then i need to turn off the computer and turn on to fix.
while i don't close the first gnome session doesn't pass anything.
the problem is when close the gnome session and go to gdm.

my laptop is IBM Thinkpad a21p
my lspci is:
0000:00:00.0 Host bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
0000:00:01.0 PCI bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
0000:00:02.0 CardBus bridge: Texas Instruments PCI1450 (rev 03)
0000:00:02.1 CardBus bridge: Texas Instruments PCI1450 (rev 03)
0000:00:03.0 Ethernet controller: Intel Corp. 82557/8/9 [Ethernet Pro 100] (rev 09)
0000:00:03.1 Serial controller: Xircom Mini-PCI V.90 56k Modem
0000:00:05.0 Multimedia audio controller: Cirrus Logic CS 4614/22/24 [CrystalClear SoundFusion Audio Accelerator] (rev 01)
0000:00:07.0 Bridge: Intel Corp. 82371AB/EB/MB PIIX4 ISA (rev 02)
0000:00:07.1 IDE interface: Intel Corp. 82371AB/EB/MB PIIX4 IDE (rev 01)
0000:00:07.2 USB Controller: Intel Corp. 82371AB/EB/MB PIIX4 USB (rev 01)
0000:00:07.3 Bridge: Intel Corp. 82371AB/EB/MB PIIX4 ACPI (rev 03)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Rage Mobility M3 AGP 2x (rev 02)


please help me.[/QUOTE]

Do you have anything in the PCMCIA slot ?
Try adding this line to /etc/pcmcia/config.opts
   exclude irq 9
Then shutdown, wait 10 secs and reboot.
I am not sure, but it may be that for some reason the sound card is on irq 9 instead of irq 5
I have an A21p at work and will see if I can duplicate the problem.

- Robert

---

### Post by olivierD on 2004-10-26
Please test this :

edit your kernel command line and replace "acpi=on" by "acpi=force" in /boot/grub/menu.lst and reboot
i have the same message but for a wireless pcmcia card on my gericom laptop.

OlivierD

---

### Post by voyaman on 2004-10-26
anything of you tell me work:

i receive the same error.

i'll try with "pci=biosirq".

and i'll continue searching a solution to this problem, when find it, i'll post it.

---

