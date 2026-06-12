---
title: "UPS battery not loading"
date: 2010-02-20
forum: Hardware
---

### Post by emma_peel on 2010-02-20
Hello dear forum.

I'm trying to handle my UPS using NUT. The installation has been done without any issues. The UPS is an APC Back-UPS ES 550.

The first problem is that the LOWBAT status, even displayed by upsc, does not seem to be catched by the daemon. The UPS went out of power without shutting down the computer (which were plugged on another line).

On the first try, the charge level dropped until 15 % ... and stayed at this level for a long time. After a while, the charge dropped very quickly. I can no longer load the battery now :

```
emma@Alanine:/dev/bus/usb/002$ upsc myups
battery.charge: 0
battery.charge.low: 10
battery.charge.warning: 50
...
ups.status: OL CHRG LB
...

```

When I unplug the UPS, the charge level is raised at 15 % ... the charge is going until 0 % without shutting down the computer.

I tried to acpupsd also, with the same result.

My battery is becoming old, about 2,5 year. It may be time to change it. This UPS is supposed is raised on alert (red LED), but anything has been displayed.

What do you suggest ? Change the battery ? Can this behavior may be due to some software bug or misuse ?

Thank you for your help !

---

### Post by emma_peel on 2010-02-22
Finally did another try and everything went right.

I think it is good to test the UPS and empty the battery from times to times.

---

