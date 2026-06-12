---
title: "Asrock Alive NF6G &amp; ACPI wakealarm"
date: 2013-08-01
forum: Hardware
---

### Post by chipdaz on 2013-08-01
Please help. I'd like to know if anyone has got acpi wakeup to work using any Alive NF6G board (most interested in the NF6G-GLAN) or anyone can see any problems with the following.

I've followed the instructions from [http://www.mythtv.org/wiki/ACPI_Wakeup](http://www.mythtv.org/wiki/ACPI_Wakeup).

When I do this bit:

echo 0 > /sys/class/rtc/rtc0/wakealarm
echo `date '+%s' -d '+ 5 minutes'` > /sys/class/rtc/rtc0/wakealarm
cat /sys/class/rtc/rtc0/wakealarmAnd check /proc/driver/rtc I get:

rtc_time    : 09:25:13
rtc_date    : 2013-08-01
alrm_time    : 09:28:51
alrm_date    : 2013-08-01
alarm_IRQ    : yes
alrm_pending    : no
update IRQ enabled    : no
periodic IRQ enabled    : no
periodic IRQ frequency    : 1024
max user IRQ frequency    : 64
24hr        : yes
periodic_IRQ    : no
update_IRQ    : no
HPET_emulated    : no
BCD        : yes
DST_enable    : no
periodic_freq    : 1024
batt_status    : okay

which looks ok to me but the alarm time passes with no wakeup. The RTC is set to UTC. 

I've also enabled everything in /proc/acpi/wakeup and fiddled about with enabling and disabling RTC alarm on in the bios but nothing seems to get the computer to wake from standby or .

Also "dmesg | grep rtc" gives:

[    0.787753] rtc_cmos 00:01: RTC can wake from S4
[    0.787996] rtc_cmos 00:01: rtc core: registered rtc_cmos as rtc0
[    0.788133] rtc_cmos 00:01: alarms up to one year, y3k, 114 bytes nvram



but setting the alarms day/time in the bios menu (which works) only offers "every day" or a fixed day each month which makes me think that it might not actually be able to do alarms up to one year.

I'm hoping to get mythtv to automatically set the next wakeup time via mythwelcome for dvb tv recording.

I'm grateful for all help or suggestions.

Kind regards,

Darren Wilkinson

---

