---
title: "automatic wake up"
date: 2009-10-03
forum: Hardware
---

### Post by kalug on 2009-10-03
Hi all out there,

I have a MS-1221 mobo and in BIOS there is no entry like APM. Still, I want my notebook to wake up on certain days at 3 o'clock (automatically). Is there any way to do this? I've tried nvram-wakeup but I get the following .conf file (genereted by guess-helper):

################################################
##  Mainboard autodetection information:
##
##    - Mainboard vendor:   "MSI"
##    - Mainboard type:     "MS-1221"
##    - Mainboard revision: "Ver 1.000"
##    - BIOS vendor:        "American Megatrends Inc."
##    - BIOS version:       "A1221IG6 V1.1"
##    - BIOS release:       "05/28/2007"

And when I just write in the terminal:
sudo nvram-wakeup -s $((`date +%s` + 20 * 60))
I get the following errormsg:
/dev/mem: Operation not permitted

I have read somewhere that not all mobos are able to wake up automatically from a soft-off state... how can I find out whether mine is one of those?

I appreciate any critical question or help.

Thanks

---

### Post by Lampi on 2009-10-03
dmesg | grep rtc should tell you sth like this
```
[    3.904592] rtc_cmos 00:05: RTC can wake from S4
[    3.904627] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    3.904654] rtc0: alarms up to one month, y3k, 114 bytes nvram
[    3.906592] Using IPI No-Shortcut mode
[    3.906908] rtc_cmos 00:05: setting system clock to 2009-10-03 09:02:32 UTC (1254560552)
```
but then again: if you have no power management settings in your BIOS this might not work, usually you should be able to set a timer in BIOS as well, cuz that's where acpi-wakeup will be trying to write to

---

