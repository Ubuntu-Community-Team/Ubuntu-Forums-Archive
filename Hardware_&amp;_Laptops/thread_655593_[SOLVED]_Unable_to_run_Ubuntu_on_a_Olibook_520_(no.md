---
title: "[SOLVED] Unable to run Ubuntu on a Olibook 520 (notebook)"
date: 2008-01-01
forum: Hardware &amp; Laptops
---

### Post by Ropechoborra on 2008-01-01
Hi, I recently bought a Olivetti 520 notebook.

I'm trying to run Ubuntu 7.04 Live and it just hungs up after selecting "Start or Install ubuntu" 
I also tryed noapic nolapic no_timer_check safe graphics but nothing happend.
The weired thing is that if a Virtualice Ubuntu from Windows Vista with VirtualBox, it works. (but without sound)

What can i do? 


[B]System Details:

Manufacturer: SICSA
Processor: Intel Pentium Dual CPU T2310 1.46 1.47
1Gb ram ddr2
VGA: SiS 307ELV
Audio Realtek ALC662
LAN Realtek RTL8201CL
Modem Motorola
WLAN LiteOn WN6301L
Card Reader: Realtek RTL5158[/B]



Loading ubuntu 7.04 live : Last commands in console.

[I][ 2.672626] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[ 2.672789] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[ 2.672953] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[ 2.673120] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[ 2.676243] ACPI: Thermal Zone [TZ01] (51 C)
[ 3.656000] Time: acpi_pm clocksouyrce has been installed.
Donde.
Begin: Mounting root file system... ...
[ 3.980000] SIS5513: IDE controller at PCI slot 0000:00:02.5
[ 3.980000] ACPI: PCI Interrupt 0000:00:03.0[A] -> GSI 20 (level, low) -> IRQ 16
[ 3.980000] SIS5513: chispet revision 1
[ 3.980000] SIS5513: not 100% native mode: will probe irqs later
[ 3.980000] SIS5513: SiS968 ATA 133 (2nd gen) controller
[ 3.980000] ide0: BM-DMA at 0x1080-0x108, Bios settings: hda:DMA, hdb:pio
[ 4.192000] usbcore: registered new interface driver usbfs
[ 4.192000] usbcore: registered new interface driver hub
[ 4.192000] usbcore: registered new device driver usb
[ 4.192000] SCSI subsystem initialized[/I]

The same but in safe graphics mode:
[I]
[ 2.672626] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[ 2.672789] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[ 2.672953] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[ 2.673120] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[ 2.676243] ACPI: Thermal Zone [TZ01] (51 C)
[ 3.656000] Time: acpi_pm clocksouyrce has been installed.
Donde.
Begin: Mounting root file system... ...
[ 4.192000] usbcore: registered new interface driver usbfs
[ 4.192000] usbcore: registered new interface driver hub
[ 4.192000] usbcore: registered new device driver usb
[ 4.196000] ACPI: PCI Interrupt 0000:00:03.0[A] -> GSI 20 (level, low) -> IRQ 16
[ 4.196000] ohci_hcd 0000:00:03.0: OHCI Host Controller
[ 4.196000] ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus number 1
[ 4.196000] ohci_hcd 0000:00:03.0: irq 16, io mem 0xd4104000
[ 4.308000] usb usb1: configuration #1 chosen from 1 choice
[ 4.308000] hub 1-0:1.0: USB hub found
[ 4.308000] hub 1-0:1.0: 4 ports detected[/I]

---

### Post by juanlb on 2008-01-01
I have the same problem with the same notebook.

Now I'm downloading the version "alternate" of Ubuntu, wich comes without live CD.

If it is succesfully, I'll will post it.

---

### Post by Ropechoborra on 2008-01-06
Well, updateing: Not working with alternate Cd.

I found a Knoppix 5.0 live cd that i had and it works fine.

Im just lost.

---

### Post by juanlb on 2008-01-11
I finally get it work with the followings kernel parameters:

noapic nolapic acpi=off irqpoll

---

### Post by Ropechoborra on 2008-01-12
Thank you very much, that solved my problem :)

---

### Post by chadjohnson on 2008-03-02
To fix the "AE_NOT_FOUND, Processor Device is not present" issue on OpenSUSE, I compiled an installed into initramfs a new custom DSDT. See [http://ubuntuforums.org/showthread.php?t=609925](http://ubuntuforums.org/showthread.php?t=609925).

---

