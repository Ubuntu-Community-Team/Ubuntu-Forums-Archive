---
title: "battery monitor not working in 9.04"
date: 2009-06-14
forum: Hardware
---

### Post by keratos on 2009-06-14
searched:

[urlhttp://ubuntuforums.org/showthread.php?t=1155641&highlight=battery+monitor+recognize+plugged+in&page=1[/url]

[http://ubuntuforums.org/showthread.php?t=1177515&highlight=battery+monitor+plugged](http://ubuntuforums.org/showthread.php?t=1177515&highlight=battery+monitor+plugged)

I'm using kubuntu jaunty on my Toshiba A300 laptop and the battery monitor system tray applet detects running on AC power or battery power, at poweron. If I change the power source after startup then there battery monitor does not chnage. For example: Running on battery power for 2hrs. Meessage appears relating to low-battery, so I switch to mains power yet the battery monitor shows a battery bar (not plugged in). Strangely the battery charges up and this is confirmed by the slowly increasing battery power bars on the display, as the battery charges.

My current kernel is 2.6.20-rc6 with  "Power Options and apci options" as follows:
```

#
# Power management and ACPI options
#
CONFIG_PM=y
# CONFIG_PM_DEBUG is not set
CONFIG_PM_SLEEP_SMP=y
CONFIG_PM_SLEEP=y
CONFIG_SUSPEND=y
CONFIG_SUSPEND_FREEZER=y
CONFIG_HIBERNATION=y
CONFIG_PM_STD_PARTITION=""
CONFIG_ACPI=y
CONFIG_ACPI_SLEEP=y
# CONFIG_ACPI_PROCFS is not set
# CONFIG_ACPI_PROCFS_POWER is not set
CONFIG_ACPI_SYSFS_POWER=y
CONFIG_ACPI_PROC_EVENT=y
CONFIG_ACPI_AC=m
CONFIG_ACPI_BATTERY=m
CONFIG_ACPI_BUTTON=m
CONFIG_ACPI_VIDEO=m
CONFIG_ACPI_FAN=m
CONFIG_ACPI_DOCK=y
CONFIG_ACPI_PROCESSOR=m
CONFIG_ACPI_HOTPLUG_CPU=y
CONFIG_ACPI_THERMAL=m
# CONFIG_ACPI_CUSTOM_DSDT is not set
CONFIG_ACPI_BLACKLIST_YEAR=0
# CONFIG_ACPI_DEBUG is not set
CONFIG_ACPI_PCI_SLOT=m
CONFIG_X86_PM_TIMER=y
CONFIG_ACPI_CONTAINER=m
CONFIG_ACPI_SBS=m
CONFIG_X86_APM_BOOT=y
CONFIG_APM=y
# CONFIG_APM_IGNORE_USER_SUSPEND is not set
CONFIG_APM_DO_ENABLE=y
# CONFIG_APM_CPU_IDLE is not set
# CONFIG_APM_DISPLAY_BLANK is not set
# CONFIG_APM_ALLOW_INTS is not set

```

No messages in /var/log files regarding switch to AC power.

Any ideas?

---

