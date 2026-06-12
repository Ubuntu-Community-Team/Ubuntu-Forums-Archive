---
title: "Unable to use Wake Alarm on Vostro 1014 Ubuntu Dell BIOS A02"
date: 2010-07-08
forum: Hardware
---

### Post by sohelmk on 2010-07-08
Hi,

I am using Dell Vostro 1014 with Ubuntu 10.04 and Dell BIOS version A02.  I
want to use ACPI wake alarm to start machine at specific time. Followed  all
steps listed below, but machine never starts. The machine does support  ACPI
from the output of dmidecode command, but in the BIOS I did not find any
option to enable/disable this, though there are options to enable "wake   on
USB" and "wake on LAN". I wonder if this is BIOS issue or something  else. If
I set the alarm using this method and restart manually the alarm time is
correct, but date gets distored..like **.**

Any help to debug or fix this issue would be greatly appreciated.

Steps I did :
1. added the HWCLOCKACCESS variable to /etc/default/rcS :  HWCLOCKACCESS=no

2.change the script /etc/init/hwclock-save.conf, to not update BIOS time  on
shutdown

    if [ "$HWCLOCKACCESS" != "no" ]; then
        exec hwclock --rtc=/dev/rtc0 --systohc $tz --noadjfile $badyear
    fi
end script

3. Ran following commands (ref: ubuntuforums )

sudo sh -c "echo 0 > /sys/class/rtc/rtc0/wakealarm"
sudo sh -c "echo `date '+%s' -d '+ 5 minutes'` >
/sys/class/rtc/rtc0/wakealarm"
cat /sys/class/rtc/rtc0/wakealarm
cat /proc/driver/rtc
{ shows following output
rtc_time    : 19:35:55
rtc_date    : 2010-07-08
alrm_time    : 19:38:44
alrm_date    : 2010-07-08
alarm_IRQ    : yes
alrm_pending    : no
24hr        : yes
periodic_IRQ    : no
update_IRQ    : no
HPET_emulated    : no
DST_enable    : no
periodic_freq    : 1024
batt_status    : okay
}

sudo shutdown -h now

Attached are all commands output on system hardware (lspci, dmidecode,  dmesg
etc)

Please let me know if you need any other info

Many thanks,
Sohel

---

