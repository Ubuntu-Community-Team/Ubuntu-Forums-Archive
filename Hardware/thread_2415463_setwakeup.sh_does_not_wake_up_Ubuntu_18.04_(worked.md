---
title: "setwakeup.sh does not wake up Ubuntu 18.04 (worked in 14.04 on the same machine)"
date: 2019-03-26
forum: Hardware
---

### Post by jhmgbl on 2019-03-26
My motherboard is ASUS M5A78L-M/USB3. My setwakeup.sh is as follows:

```
#!/bin/sh
#
# set ACPI Wakeup time
# usage: setwakeup.sh seconds
#    seconds - number of seconds from epoch to UTC time (time_t time format)
#
# set UTCBIOS to true if bios is using UTC time
# set UTCBIOS to false if bios is using local time

UTCBIOS=true

if $UTCBIOS
then
    #utc bios - use supplied seconds
    SECS=$1
else
    #non utc bios - convert supplied seconds to seconds from
    #epoch to local time
    SECS=`date -u --date "\`date --date @$1 +%F" "%T\`" +%s`
fi

#echo 0 > /sys/class/rtc/rtc0/wakealarm    # clear alarm
#echo $SECS > /sys/class/rtc/rtc0/wakealarm   # write the waketime
/usr/sbin/rtcwake --mode no --time $SECS



```

---

