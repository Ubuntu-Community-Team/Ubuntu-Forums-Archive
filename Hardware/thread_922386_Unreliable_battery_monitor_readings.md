---
title: "Unreliable battery monitor readings"
date: 2008-09-17
forum: Hardware
---

### Post by Nuckinfuts on 2008-09-17
Ubuntu 7.10 fully updated, ZT Systems MS1424 laptop

my battery monitor in gnome fails to read at times and fades in and out between reading and not.  For example; it may show battery charge correctly for 10-20 minutes, then show "-:--" and 0% charge for a little while and then come back.

i can give more specs if needed
and thank you in advance! =)

---

### Post by Nuckinfuts on 2008-10-02
im forced to /bump

---

### Post by Nuckinfuts on 2009-01-28
So, I am now on 8.10, still with the same issue, with the added effect of the laptop shutting down randomly when on battery power.  By shutting down I don't mean power loss, it literally just goes through the shutdown procedures and powers off.

I have reset all my power management options to Suspend/Hibernate/Shutdown never.

acpitool output:
```
nuckinfuts@nuckinfuts-laptop:~$ acpitool -aB
  Battery #1     : present
    Remaining capacity : unknown, 0.00%
    Design capacity    : 4400 mAh
    Last full capacity : 2495 mAh, 56.7% of design capacity
    Capacity loss      : 43.3%
    Present rate       : 0      
    Charging state     : charged
    Battery type       : rechargeable, 
    Model number       : MS-1414
    Serial number      : MS-1414
  AC adapter     : off-line

```

This is while AC power is plugged in and Gnome's notification area icon shows 99.7% power and AC power plugged in.  The stand alone applet however shows 0% battery.

Not sure if it is related but Suspend goes to black screen, turns off the display, then turns it back on to a black screen with no mouse.  Only way to escape from the black screen is a hard-boot.  Hibernate causes Bluetooth issues on reboot even though i have disabled bluetooth and do not have the hardware.

---

