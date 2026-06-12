---
title: "Can't control screen brightness on LG 300"
date: 2008-09-10
forum: Hardware
---

### Post by NickEvans on 2008-09-10
The screen brightness buttons do not work on my LG E300 laptop.

Here is the output from gnome-power-bugreport.sh:
> Distro version:       DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.04
DISTRIB_CODENAME=hardy
DISTRIB_DESCRIPTION="Ubuntu 8.04.1"
Kernel version:       2.6.24-21-generic
g-p-m version:        2.22.1
HAL version:          0.5.11rc2
System manufacturer:  missing
System version:       missing
System product:       missing
AC adapter present:   yes
Battery present:      yes
Laptop panel present: no
CPU scaling present:  yes
Battery Information:
  battery.charge_level.current = 43212  (0xa8cc)  (int)
  battery.charge_level.design = 48840  (0xbec8)  (int)
  battery.charge_level.last_full = 47652  (0xba24)  (int)
  battery.charge_level.percentage = 90  (0x5a)  (int)
  battery.charge_level.rate = 18492  (0x483c)  (int)
  battery.is_rechargeable = true  (bool)
  battery.model = 'BAT1'  (string)
  battery.present = true  (bool)
  battery.rechargeable.is_charging = true  (bool)
  battery.rechargeable.is_discharging = false  (bool)
  battery.remaining_time = 864  (0x360)  (int)
  battery.reporting.current = 3893  (0xf35)  (int)
  battery.reporting.design = 4400  (0x1130)  (int)
  battery.reporting.last_full = 4293  (0x10c5)  (int)
  battery.reporting.rate = 1666  (0x682)  (int)
  battery.reporting.technology = 'Li-ion'  (string)
  battery.reporting.unit = 'mAh'  (string)
  battery.technology = 'lithium-ion'  (string)
  battery.type = 'primary'  (string)
  battery.vendor = ' LG'  (string)
  battery.voltage.current = 12528  (0x30f0)  (int)
  battery.voltage.design = 11100  (0x2b5c)  (int)
  battery.voltage.unit = 'mV'  (string)
GNOME Power Manager Process Information:
nick      6228  0.0  0.4  72152 15360 ?        Ssl  Sep09   0:02 gnome-power-manager
HAL Process Information:
111       5553  0.0  0.1   6324  4324 ?        Ss   Sep09   0:02 /usr/sbin/hald
root      5557  0.0  0.0   3352  1156 ?        S    Sep09   0:00  \_ hald-runner
root      5630  0.0  0.0   3416  1164 ?        S    Sep09   0:01      \_ hald-addon-input: Listening on /dev/input/event8 /dev/input/event1 /dev/input/event3 /dev/input/event4 /dev/input/event5 /dev/input/event6
root      5639  0.0  0.0   3428  1224 ?        S    Sep09   0:00      \_ /usr/lib/hal/hald-addon-cpufreq
111       5640  0.0  0.0   2204   960 ?        S    Sep09   0:00      \_ hald-addon-acpi: listening on acpid socket /var/run/acpid.socket
root      5664  0.0  0.0   3420  1140 ?        S    Sep09   0:03      \_ hald-addon-storage: polling /dev/scd0 (every 2 sec)


---

### Post by ice2921 on 2008-09-10
I have the same issue on my Toshiba I hope someone can help us.

---

### Post by NickEvans on 2008-09-11
Bump...

---

### Post by J-Morris on 2008-09-11
I also have this problem with my HP pavilion dv2000

---

### Post by Mr. Mullrway on 2008-09-11
I would be interested in the answer to this as well.  I have been having a similar problem.

---

### Post by NickEvans on 2008-11-02
Fixed with update to Intrepid :D

---

### Post by usualsuspect00 on 2008-11-04
That means your keyboard worked right out of the box?? Mine is like FROZEN.

If you know anything about that, please inform me

---

