---
title: "Battery monitoring shot on HP ze4400 Gutsy"
date: 2007-11-19
forum: Hardware &amp; Laptops
---

### Post by sticksabuser on 2007-11-19
Hi all,

I recently managed to fix a friend's HP laptop (pavilion ze4400) and wiped the hard drive and then installed gutsy. First I had some issues with partitioning. I usually manually partition the HDD coz I like to have a larger swap partition (~2GB). I had the swap configured in as a primary partition in the beginning of the hard drive and the rest as the / partition configured as a logical partition. So apparently this wasn't correct coz the performance was less than spectacular. At that point though, battery monitoring seemed to be working fine. So I reformatted, had the beginning of the hard drive configured for / and the partition was set to bootable and and set as a primary partition. The swap partition was set to a logical partition. The following is the current partition info:

> steve@metalrulez:~$ sudo fdisk -l
[sudo] password for steve:

Disk /dev/hda: 30.0 GB, 30005821440 bytes
255 heads, 63 sectors/track, 3648 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xceffceff

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3404    27342598+  83  Linux
/dev/hda2            3405        3648     1959930    5  Extended
/dev/hda5            3405        3648     1959898+  82  Linux swap / Solaris

So now battery monitoring always shows 0%. The following are some outputs that I hope would help. Thanks

> steve@metalrulez:~$ gnome-power-bugreport.sh

Distro version:       DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=7.10
DISTRIB_CODENAME=gutsy
DISTRIB_DESCRIPTION="Ubuntu 7.10"
Kernel version:       2.6.22-14-generic
g-p-m version:        2.20.0
HAL version:          0.5.9.1
System manufacturer:  Hewlett-Packard
System version:       KAM1.44
System product:       Pavilion ze4400 (DL682AV)
AC adapter present:   yes
Battery present:      yes
Laptop panel present: no
CPU scaling present:  yes
Battery Information:
  battery.charge_level.capacity_state = 'ok'  (string)
  battery.charge_level.current = 0  (0x0)  (int)
  battery.charge_level.design = 65120  (0xfe60)  (int)
  battery.charge_level.granularity_1 = 473  (0x1d9)  (int)
  battery.charge_level.granularity_2 = 473  (0x1d9)  (int)
  battery.charge_level.last_full = 42624  (0xa680)  (int)
  battery.charge_level.low = 2960  (0xb90)  (int)
  battery.charge_level.rate = 2368  (0x940)  (int)
  battery.charge_level.unit = 'mWh'  (string)
  battery.charge_level.warning = 4440  (0x1158)  (int)
  battery.is_rechargeable = true  (bool)
  battery.model = '01KT'  (string)
  battery.present = true  (bool)
  battery.rechargeable.is_charging = true  (bool)
  battery.rechargeable.is_discharging = false  (bool)
  battery.remaining_time = 64800  (0xfd20)  (int)
  battery.reporting.current = 0  (0x0)  (int)
  battery.reporting.design = 4400  (0x1130)  (int)
  battery.reporting.granularity_1 = 32  (0x20)  (int)
  battery.reporting.granularity_2 = 32  (0x20)  (int)
  battery.reporting.last_full = 2880  (0xb40)  (int)
  battery.reporting.low = 200  (0xc8)  (int)
  battery.reporting.rate = 160  (0xa0)  (int)
  battery.reporting.technology = 'LION'  (string)
  battery.reporting.unit = 'mAh'  (string)
  battery.reporting.warning = 300  (0x12c)  (int)
  battery.serial = '7'  (string)
  battery.technology = 'lithium-ion'  (string)
  battery.type = 'primary'  (string)
  battery.vendor = 'SMP'  (string)
  battery.voltage.current = 16864  (0x41e0)  (int)
  battery.voltage.design = 14800  (0x39d0)  (int)
  battery.voltage.unit = 'mV'  (string)
GNOME Power Manager Process Information:
steve     5184  0.0  5.2  37236 11772 ?        Ss   12:43   0:00 gnome-power-manager
HAL Process Information:
107       4472  0.0  1.6   5660  3760 ?        Ss   12:43   0:00 /usr/sbin/hald
root      4473  0.0  0.4   3092  1032 ?        S    12:43   0:00  \_ hald-runner
107       4526  0.0  0.4   2160   896 ?        S    12:43   0:00      \_ hald-addon-keyboard: listening on /dev/input/event1
107       4529  0.0  0.4   2160   892 ?        S    12:43   0:00      \_ hald-addon-keyboard: listening on /dev/input/event4
107       4530  0.0  0.3   2156   888 ?        S    12:43   0:00      \_ hald-addon-keyboard: listening on /dev/input/event5
root      4536  0.0  0.4   3156  1108 ?        S    12:43   0:00      \_ /usr/lib/hal/hald-addon-cpufreq
107       4537  0.0  0.4   2160   920 ?        S    12:43   0:00      \_ hald-addon-acpi: listening on acpid socket /var/run/acpid.socket
107       4539  0.0  0.4   2160   892 ?        S    12:43   0:00      \_ hald-addon-keyboard: listening on /dev/input/event6
107       4607  0.0  0.5   3260  1188 ?        S    12:43   0:00      \_ hald-addon-storage: polling /dev/hdc (every 2 sec) 

> cat /proc/acpi/battery/BAT1/state

present:                 yes
capacity state:          ok
charging state:          discharging
present rate:            1120 mA
remaining capacity:      unknown
present voltage:         15584 mV

> cat /proc/acpi/battery/BAT1/state

present:                 yes
capacity state:          ok
charging state:          charged
present rate:            0 mA
remaining capacity:      unknown
present voltage:         16480 mV

>  cat /proc/acpi/battery/BAT1/info

present:                 yes
design capacity:         4400 mAh
last full capacity:      2880 mAh
battery technology:      rechargeable
design voltage:          14800 mV
design capacity warning: 300 mAh
design capacity low:     200 mAh
capacity granularity 1:  32 mAh
capacity granularity 2:  32 mAh
model number:            01KT
serial number:           7
battery type:            LION
OEM info:                SMP


---

### Post by sticksabuser on 2007-11-19
bump

---

### Post by sticksabuser on 2007-11-19
Anyone?

---

