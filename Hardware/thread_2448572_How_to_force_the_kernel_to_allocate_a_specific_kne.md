---
title: "How to force the kernel to allocate a specific knernel module to a specific device"
date: 2020-08-10
forum: Hardware
---

### Post by pascalcnrad on 2020-08-10
Of course, some of you might question why I have posted this here  instead of the subforum for Macs. It's because there won't be a  hardware based solution and so, my question doesn't directly refer to hardware. There is no hardware/firmware based solution because Macs don't have a EFI-Setup where one could easily switch between IDE and AHCI.
Therefore, I aspire to find a software based solution.

I have an old iMac from 2010 here. It shall run Ubuntu 20.04 Focal  Fossa with an SSD. 
Unfortunately, the readeon driver does not support the EFI-Boot of the  GPU (Radeon HD 4670). So, I obligatorily have to use Ubuntu in BIOS mode. That's isn't a  deep problem because almost all the hardware works very fine out of the  box in BIOS mode. 
But, due to the fact that the iMac aspires to support Windows XP, when booting up in BIOS mode the SATA-Controller pretends to be an  IDE-Interface. This isn't an issue as one uses just a slow HDD. But, SSDs do really take  benefit of the AHCI mode.

On Windows, this is solved by Apple's Boot Camp Setup which forces Windows to treat the Controller as an AHCI-Controller.

 Therefore, I intend to do the same on Linux. I want to force the kernel (5.4.0-42) to use an ahci driver for the  SATA-Controller with an adress that I'm conscious about. 
I had already found an old article published in 2005 referring to a  similar issue with a USB device. But, it refers to edit in the »/sys/« directory which is frequently emptied at shutdown. So, this doesn't work in 2020  on Focal Fossa. So, how can I achieve to make the kernel load the AHCI driver and bind it instead of the IDE driver although the device pretends to be and IDE Interface.

---

### Post by TheFu on 2020-08-10
/sys is a pseudo-file system. It doesn't really exist. It is only created and presented by the kernel.
You might try blacklisting the IDE driver and using options with the SATA driver.

I don't know that GPUs care at all about the boot mode.  My GPU drivers aren't loaded by Linux until well after boot, but I really don't know. Macs are funny.

---

### Post by pascalcnrad on 2020-08-10
Hey, thank @TheFu
Of course, GPUs care a lot about the boot mode. For example, there some extra „Mac graphics cards“ out there, that are built to have a boot screen and some other stuff on Macs.
referring to special „Mac Graphics Cards“ is often recommended to flash a grahics card intending to make it Mac-compatible.
The only thing that I have figured out is: As I boot up the iMac without »nomodeset« via EFI BOOT I get a black screen. As I boot up the iMac in BIOS mode everything works fine.
But, that's not the subject.
According to „lspci -v “ ,there are two drivers loaded for the IDE-Interface. The first one ist „ata_piix“, which is a built-in-driver. The second one is „pata_acpi“ which is a dedicated module.
Do I have to substitute both of them? How to do?

---

### Post by pascalcnrad on 2020-08-10
I'm done trying out blacklisting. I've tried both blacklisting via »/etc/default/grub« and via »/etc/modprobe.d/blacklist«.
Of course, I have done »sudo update-initramfs -u« and »sudo update-grub« both trials.
But, it doesn't have any impact. The emit of »lspci -v« is still the same what means that the kernel driver is still „ata_piix“ and the kernel module is still „pata_acpi“.

---

### Post by TheFu on 2020-08-10
I don't think either of those are loadable modules.  PIIX is a southbridge, I think.
You've probably seen these links already:
[LIST]
[*][https://ata.wiki.kernel.org/index.php/Ata_piix](https://ata.wiki.kernel.org/index.php/Ata_piix)
[*][https://ata.wiki.kernel.org/index.php/Pata_acpi](https://ata.wiki.kernel.org/index.php/Pata_acpi)
[/LIST]

When I said that video drivers aren't loaded until well after boot, I meant that only simple VESA drivers are assumed prior, so we get a grub screen.  Again, no clue what a Mac does.

---

### Post by pascalcnrad on 2020-08-10
> I don't think either of those are loadable modules.  PIIX is a southbridge, I think.
As far as I know know &#8222;ata_piix&#8220; isn't a dedicated loadable module because it's built-in.
But, &#8222;pata_acpi&#8220; is listed as a loadable module according to &#8222;modinfo pata_acpi&#8220;. It's not worth worth to post that here because everyone can do it himself.

The relevant part of &#8222;lspci -v&#8220; referring to my problem:
```
00:1f.2 IDE interface: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA IDE Controller (rev 06) (prog-if 8f [PCI native mode controller, supports both channels switched to ISA compatibility mode, supports bus mastering])
    Subsystem: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA IDE Controller
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
    I/O ports at 3128 [size=8]
    I/O ports at 3134 [size=4]
    I/O ports at 3120 [size=8]
    I/O ports at 3130 [size=4]
    I/O ports at 3020 [size=16]
    I/O ports at ffe0 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: ata_piix
    Kernel modules: pata_acpi
```

---

### Post by Yellow Pasque on 2020-08-11
> On Windows, this is solved by Apple's Boot Camp Setup which forces Windows to treat the Controller as an AHCI-Controller.

If you can give a link that has more technical info on ^that, it might be helpful for those of us not familiar with Macs.

---

