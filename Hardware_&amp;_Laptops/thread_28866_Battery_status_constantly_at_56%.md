---
title: "Battery status constantly at 56%"
date: 2005-04-21
forum: Hardware &amp; Laptops
---

### Post by benrose on 2005-04-21
I just installed Ubuntu Hoary 5.04 on my HP Pavilion ze4365, and virtually everything worked straight out of the box. I say virtually because for some reason my battery charge monitor is stuck saying the battery is at 56% charged and is in the process of charging, even when I unplug the AC source. My LEDs on my laptop correctly display orange while charging and eventually turned green to indicate the battery is fully charged, but no change in the battery meter. The only thing I found that looked suspicious is in /var/log/syslog there are a lot of lines that read...

> battery-stats-collector[31223]: apm_read failed with error code 1 

Any help would be greatly appreciated, as this is the only issue keeping me from using my laptop everywhere I go.

---

### Post by benrose on 2005-04-21
I just discovered the first lines proceeding the read errors are as follows... 

> kernel: apm: BIOS not found

I feel like Im getting close but still missing something....

---

### Post by alastair on 2005-04-22
I'm not sure APM is used (by default) - but ACPI. ACPI takes care of power management, battery, suspend etc.

Have a closer look through your log :

/var/log/syslog

and check, from boot, for ACPI messages (perhaps you will notice "BATT" or something as well).

---

### Post by benrose on 2005-04-22
Well it seems it be able to detect when I have AC power plugged in and when its running off of battery now, but the battery level is either 0% or 100% now. 

It seems ACPI does find my battery... as this is the line in /var/log/syslog...

> Apr 22 13:53:01 localhost kernel: ACPI: Battery Slot [BAT1] (battery present)


But my /proc/acpi/battery/BAT1/state file looks like this...

> present:                 yes
capacity state:          ok
charging state:          charging
present rate:            1984 mA
remaining capacity:      3328 mAh
present voltage:         16768 mV

Under remaining capacity it mentions 3328mAh, while my battery is rated for 4400mAh. I took the battery out and hit the button on it and it registered barely 20% of charge. Yet my Battery Charge Monitor is showing a 100% charge.

Is it possible my battery just isn't calibrated? I haven't used this laptop in awhile. I would be willing to reinstall Windows for a bit just to get the tools to recalibrate it if anyone felt it would change anything.

Thanks for any help!!

---

