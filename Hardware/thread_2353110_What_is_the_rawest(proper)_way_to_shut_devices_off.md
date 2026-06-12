---
title: "What is the rawest(proper) way to shut devices off like screen, databus, opticaldrive"
date: 2017-02-18
forum: Hardware
---

### Post by jeff666 on 2017-02-18
Ive read about a few different methods that use additional software but none of them seam like a really efficent way to work with custom scripts/services so is there a really simple way to shut devices off and turn them on during run time?

-devices i would like to be able to controll power to include:
          usb ports/ other ports
          screen
          cdrom
          data bus (that is not in use)
          ssd
          ssd/hdd bus?

a bonus would be if you could suggest a good app to manag power consumtion, thanks a ton in advance.

---

### Post by efflandt on 2017-02-20
I imagine an optical drive does not use any power when not running and an SSD does not use much power when idle (minimal mA). On the other hand a hard drive might use about 5 watts, so when running from SSD, I have a script in /etc/cron.hourly using hdparm to spin down my hard drive if idle and not mounted:```
#!/bin/sh
# Spin down drive(s) when idle and not mounted
# Put script in /etc/cron.hourly
drives="/dev/sda" # drive(s) to spin down (space separated)
IFS="$(printf '\n\t')" # remove newline from hdparm output
for hd in $drives
do
  dstate=$(/sbin/hdparm -C $hd | /bin/grep -B 1 standby)
  if [ $? -ne 0 ] # if not in standby
  then # active/idle
    /bin/grep $hd /etc/mtab 2>&1 > /dev/null
    if [ $? -ne 0 ] # do standby if not mounted
    then dstate=$(/sbin/hdparm -y $hd 2>&1)
    fi 
  fi
  if [ "$dstate" != '' ] # log unless mounted (null)
    then echo $dstate | /usr/bin/logger -e
  fi
done
```If using X, the Brightness & Lock setting can turn off your monitor after a period of inactivity, or from terminal window: **xset dpms force standby**. However, an HDTV does not respond to dpms commands, if mine stops receiving a video signal it goes into a powersave mode for 10 minutes, then shuts off (have to manually turn it on). I don't know if Ubuntu has an app to control that using CEC over HDMI ( [https://en.wikipedia.org/wiki/Consumer_Electronics_Control](https://en.wikipedia.org/wiki/Consumer_Electronics_Control) ) like what used to be called XBMC running on a Raspberry Pi computer on a card. I used to know a shell command to shut off a laptop backlight many years ago, but forgot what it was.

I am not really concerned about my USB Logitech Unifying receiver using 98 mA and Bluetooth adapter using 100 ma (1 watt total).

I would not know how to selectively shut off parts of the bus. What do you need to leave running or could you simply put the whole computer into suspend? In a terminal see:```
apropos power
```

---

