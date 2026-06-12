---
title: "&quot;Put display to sleep when inactive for:&quot; broken after installation"
date: 2009-04-29
forum: Hardware
---

### Post by clubsoda on 2009-04-29
This works on the LiveCD but not on the hard drive installation.  The screensaver finishes and the display goes black but it doesn't actually power down.  Display sleep was functioning correctly on the same machine under Intrepid.  The Jaunty installation was "clean" except for the preservation of /home, however creating and logging into a new user account doesn't fix the problem so I'm doubtful that this is a residual configuration issue.

Hardware: AMD780 board with integrated HD3200 ATi graphics, DVI connection to BenQ LCD.

Thanks for any suggestions.

---

### Post by clubsoda on 2009-05-01
OK, it turns out that this problem only occurs when using the proprietary fglrx driver.  Maybe it is related to the following errors which appear in dmesg.```
APIC error on CPU1: 00(08)
APIC error on CPU0: 00(08)
```

Reverting to the open source radeon driver fixes both.
Can't wait for 2D acceleration in radeon for RV620 et al!

---

