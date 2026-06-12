---
title: "Packard Bell Easynote won't shut down - Feisty"
date: 2007-08-05
forum: Hardware &amp; Laptops
---

### Post by Iehova on 2007-08-05
Hi everyone,

I've had a Packard Bell Easynote MV45-008 for a good few months now, and in that time have got absolutely everything working perfectly to my liking, except for the simple act of shutting down the laptop. I have searched high and low for answers to this problem, which seems quite a popular one, and none of the answers that I've found (adding acpi=force vga=normal, nolapic (I couldn't boot then, oddly), and various combinations of apm=on acpi=off and vice-versa to the GRUB boot parameters) have made any positive difference.

IF anyone could provide any assistance, it really would be appreciated. If you need any files pasting, I'll be happy to provide. I'm really desperate to get this working. :)

---

### Post by Iehova on 2007-08-12
*Bump*

To expand on this and provide a little bit more info, i have also tried suspending and hibernating and neither of those work either. I thought that the problem might be specific to ubuntu, so I tried a few Live DVDs to see if they could manage to shut down, but none of Symphony OS, Knoppix 5.1.1, Fedora Core 6, or Gentoo 2007.0 could. In all of them though, as with ubuntu, shutdown goes perfectly _apart_ from actually powering off, for instance FC6 shows:

"Power down
sending acpi_power_off"

(That may not be exactly what it says, but as far as I remember that's it).

Really, if anyone could help it would be most appreciated. :)

---

### Post by Iehova on 2007-09-09
OK, I know this topic hasn't been posted to in four weeks, but I'm still holding out (hoping!) for an answer, and I have a little bit of extra information.

Firstly when booting (with splash screen disabled), when the kernel modules are being loaded I see the following:

apm: BIOS not found

Could this be what's stopping my computer from shutting down? Or, could it be that when shutting down 'stopping avahi_daemon' reports as having failed?

Thanks,

PS: The following may also be of some use:

> iehova@lucy-mk2:/usr/src/linux-headers-2.6.20-16-generic$ grep APM ./.config
# Power management options (ACPI, APM)
# APM (Advanced Power Management) BIOS Support
CONFIG_APM=m
# CONFIG_APM_IGNORE_USER_SUSPEND is not set
# CONFIG_APM_DO_ENABLE is not set
# CONFIG_APM_CPU_IDLE is not set
# CONFIG_APM_DISPLAY_BLANK is not set
# CONFIG_APM_RTC_IS_GMT is not set
# CONFIG_APM_ALLOW_INTS is not set
# CONFIG_APM_REAL_MODE_POWER_OFF is not set


and...

> iehova@lucy-mk2:/usr/src/linux-headers-2.6.20-16-generic$ grep ACPI ./.config# Power management options (ACPI, APM)
# ACPI (Advanced Configuration and Power Interface) Support
CONFIG_ACPI=y
CONFIG_ACPI_SLEEP=y
CONFIG_ACPI_SLEEP_PROC_FS=y
CONFIG_ACPI_SLEEP_PROC_SLEEP=y
CONFIG_ACPI_AC=m
CONFIG_ACPI_BATTERY=m
CONFIG_ACPI_BUTTON=m
CONFIG_ACPI_VIDEO=m
CONFIG_ACPI_HOTKEY=m
CONFIG_ACPI_FAN=m
CONFIG_ACPI_DOCK=m
CONFIG_ACPI_PROCESSOR=m
CONFIG_ACPI_HOTPLUG_CPU=y
CONFIG_ACPI_THERMAL=m
CONFIG_ACPI_ASUS=m
CONFIG_ACPI_IBM=m
CONFIG_ACPI_TOSHIBA=m
CONFIG_ACPI_CUSTOM_DSDT_INITRD=y
CONFIG_ACPI_BLACKLIST_YEAR=2000
# CONFIG_ACPI_DEBUG is not set
CONFIG_ACPI_EC=y
CONFIG_ACPI_POWER=y
CONFIG_ACPI_SYSTEM=y
CONFIG_ACPI_CONTAINER=m
CONFIG_ACPI_SBS=m
CONFIG_X86_ACPI_CPUFREQ=m
CONFIG_X86_POWERNOW_K7_ACPI=y
CONFIG_X86_POWERNOW_K8_ACPI=y
# CONFIG_X86_SPEEDSTEP_CENTRINO_ACPI is not set
# CONFIG_X86_ACPI_CPUFREQ_PROC_INTF is not set
CONFIG_HOTPLUG_PCI_ACPI=m
CONFIG_HOTPLUG_PCI_ACPI_IBM=m
CONFIG_PNPACPI=y
CONFIG_BLK_DEV_IDEACPI=y
CONFIG_SATA_ACPI=y
# Ubuntu ACPI added drivers
CONFIG_ACPI_PCC=m
CONFIG_ACPI_DEV=m
CONFIG_ACPI_SONY=m
CONFIG_ACPI_TC1100=m


when I run "sudo modprobe apm" I get:

> FATAL: Error inserting apm (/lib/modules/2.6.20-16-generic/kernel/arch/i386/kernel/apm.ko): No such device


The machine is an Intel Core 2 Duo running the 2.6.20.16-generic kernel.

EDIT: I have uploaded my xorg.conf, in case that is of any use.

---

