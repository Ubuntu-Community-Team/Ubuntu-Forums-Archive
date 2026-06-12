---
title: "ACPI wakealarm only after suspend/hibernate"
date: 2010-02-23
forum: Hardware
---

### Post by krabunski on 2010-02-23
Hello,

I successfully managed to make my laptop start automatically at a specified time using information from [http://www.mythtv.org/wiki/ACPI_Wakeup](http://www.mythtv.org/wiki/ACPI_Wakeup). Unfortunately it only works after a suspend or hibernate but not after a shutdown.

I have a Lenovo Thinkpad R60.

> $ cat /proc/driver/rtcrtc_time    : 12:55:03
rtc_date    : 2010-02-23
alrm_time    : 12:59:45
alrm_date    : 2010-02-23
alarm_IRQ    : yes
alrm_pending    : no
24hr        : yes
periodic_IRQ    : no
update_IRQ    : no
HPET_emulated    : yes
DST_enable    : no
periodic_freq    : 1024
batt_status    : okay
On my other IBM Thinkpad R40 acpi wakealarm works without problems after a shutdown. I can't see the difference. I also tried booting with hpet=disabled...

---

