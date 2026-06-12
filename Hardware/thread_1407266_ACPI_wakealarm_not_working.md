---
title: "ACPI wakealarm not working"
date: 2010-02-15
forum: Hardware
---

### Post by jlanza on 2010-02-15
Hi all,
I had my mythtv working properly with mythwelcome and mythshutdown (ACPI). However the other day I did something wrong and my database got corrupted. I'm running mythubuntu 9.10

This weekend I have reinstall and now the computer is not rebooting on alarms. Attached are the configuration files. 

When I run the manual commands to test the configuration:
```
 
$sudo sh -c "echo 0 > /sys/class/rtc/rtc0/wakealarm"
$sudo sh -c "echo `date '+%s' -d '+ 5 minutes'` > /sys/class/rtc/rtc0/wakealarm"
$cat /sys/class/rtc/rtc0/wakealarm
$

``` 

The last cat command should return a value, but it is not returning anything. 

When I run
```

$cat /proc/driver/rtc
rtc_time	: 01:20:00
rtc_date	: 2010-02-15
alrm_time	: 01:24:25
alrm_date	: ****-**-15
alarm_IRQ	: no
alrm_pending	: no
24hr		: yes
periodic_IRQ	: no
update_IRQ	: no
HPET_emulated	: yes
DST_enable	: no
periodic_freq	: 1024
batt_status	: okay

``` 
It seems that the alaram IRQ is not set. 

The /var/log/messages shows the ACPI is possible. And as I said I had it up an running one day before.
```
 
rtc_cmos 00:03: RTC can wake from S4
rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs

``` 
I also have added the hpet=disable to /etc/default/grub
```
 
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash hpet=disable"

``` 


Any ideas?

FILES:

/etc/default/rcS
```
 
TMPTIME=0
SULOGIN=no
DELAYLOGIN=no
#UTC=yes
UTC=no
VERBOSE=no
FSCKFIX=no
HWCLOCKACCESS=no

``` 

/etc/init/hwclock-save.conf 
```
 
description	"save system clock to hardware clock"

start on runlevel [06]

task

script
    . /etc/default/rcS
    [ "$UTC" = "yes" ] && tz="--utc" || tz="--localtime"
    [ "$BADYEAR" = "yes" ] && badyear="--badyear"
    if [ "$HWCLOCKACCESS" != "no" ]; then
       exec hwclock --rtc=/dev/rtc0 --systohc $tz --noadjfile $badyear
    fi
end script

```

---

### Post by muederkrieger on 2010-04-07
Hi,

I tried exact the same and have no success wakeup my mobo ASRock 939A785GMH/128M using S5 by "halt" or "shutdown -h now".

Using "S4" the wakeup will work:
```
echo -n "disk" > /sys/power/state
```

But the the system will not shutdown clearly (disk wasn't unmounted before ...).

Is there any fake halt-(shutdown)-command, putting the mobo in S4 instat of S5 and ignore all the resume stuff?

---

