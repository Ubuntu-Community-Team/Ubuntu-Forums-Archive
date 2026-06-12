---
title: "Ubuntu 16.04.3 on Asus Prime X399-A with AMD Ryzen 1950X"
date: 2017-12-22
forum: Hardware
---

### Post by Gijsbert_Wiesenekk on 2017-12-22
Hi,

Yesterday I tried to install Ubuntu 16.04.3 on an Asus Prime X399-A motherboard with an AMD Ryzen 1950X processor. I am using an encrypted / partition, so I am (supposed to get) prompted for the password at boot.  Installation from a bootable USB key went fine (including the prompt for the password at boot after installation), but after a couple of updates the system hang in the boot process with the error:

[FONT=courier new][Firmware Bug]: AMD-Vi: IOAPIC[130] not in IVRS table

[/FONT]I found some (older) references to this error but the suggested workarounds (like update firmware, disable IOMMU) either did not apply or did not work. I could however boot in recovery mode, resume the boot from recovery mode and got prompted for the password but now in text mode, after which the boot resumed. This suggested that the problem was perhaps somehow related to the splash screen, so I disabled splash in [FONT=courier new]/etc/default/grub[/FONT] by changing [FONT=courier new]quite splash[/FONT] to [FONT=courier new]text[/FONT] in the [FONT=courier new]GRUB_CMDLINE_LINUX_DEFAULT[/FONT] entry (Choose [FONT=courier new]Update grub bootloader[/FONT] from the recovery menu as this will remount your filesystems in [FONT=courier new]rw[/FONT] mode, choose [FONT=courier new]Drop to root shell prompt[/FONT] from the recovery meny, modify the [FONT=courier new]GRUB_CMDLINE_LINUX_DEFAULT [/FONT]entry in [FONT=courier new]/etc/default/grub[/FONT], exit and choose [FONT=courier new]Update grub bootloader[/FONT] from the recovery menu again) and although I still get the error at boot the system boots and runs fine.

FYI, I also added the option [FONT=courier new]amd_iommu_dump=1[/FONT] to [FONT=courier new]GRUB_CMDLINE_LINUX_DEFAULT[/FONT] in [FONT=courier new]/etc/default/grub[/FONT] for debugging. The [FONT=courier new]dmesg[/FONT] context of the error is:

[FONT=courier new]AMD-Vi: Using IVHD type 0x11
AMD-Vi: device: 00:00.2 cap: 0040 seg: 0 flags: b0 info 0000
AMD-Vi:        mmio-addr: 00000000ef800000
AMD-Vi:   DEV_SELECT_RANGE_START     devid: 00:01.0 flags: 00
AMD-Vi:   DEV_RANGE_END         devid: 3f:1f.6
AMD-Vi:   DEV_ALIAS_RANGE         devid: ff:00.0 flags: 00 devid_to: 00:14.4
AMD-Vi:   DEV_RANGE_END         devid: ff:1f.7
AMD-Vi:   DEV_SPECIAL(HPET[0])        devid: 00:14.0
AMD-Vi:   DEV_SPECIAL(IOAPIC[128])        devid: 00:14.0
AMD-Vi:   DEV_SPECIAL(IOAPIC[129])        devid: 00:00.1
[Firmware Bug]: AMD-Vi: IOAPIC[130] not in IVRS table
AMD-Vi: Disabling interrupt remapping
Switched APIC routing to physical flat.
[/FONT]
Regards,
Gijsbert

---

### Post by mörgæs on 2017-12-22
Thanks for posting. 
If you add to the [compatibility thread]("https://ubuntuforums.org/showthread.php?t=361236") there is a better chance that people will find your advice.

---

