---
title: "Samsung Galaxy Book2 360: spurious wakeup due to accelerometer"
date: 2023-08-22
forum: Hardware
---

### Post by andrastantos on 2023-08-22
Hello!

I have a Samsung Galaxy Book2 360 laptop. It works great under Ubuntu 22.04LTS, with one problem: when the computer goes to sleep (say, close the lid), the computer can be woken up by shaking it. This obviously isn't desired. My best guess is that it is the built-in accelerometer that wakes up the laptop.

**Here's what I know so far:**

- The interrupt for the wakeup is '14'.
- This interrupt is connected to the INTC1055 (GPIO) controller.

I haven't found a relevant entry in /proc/acpi/wakeup. Disabling every single entry in that file (except for PWRB of course) doesn't change the behavior.

Adding acpi.ec_no_wakeup argument to the boot options doesn't change the behavior.

I haven't found any wakeup-related entries in /sys/class/gpio/gpiochip664/power or under /sys/device/platform/INTC1055:00/power:

[INDENT]# ls -la /sys/class/gpio/gpiochip664/power
total 0
drwxr-xr-x 2 root root    0 Aug 22 13:50 .
drwxr-xr-x 3 root root    0 Aug 22 06:49 ..
-rw-r--r-- 1 root root 4096 Aug 22 13:50 async
-rw-r--r-- 1 root root 4096 Aug 22 13:50 autosuspend_delay_ms
-rw-r--r-- 1 root root 4096 Aug 22 13:50 control
-r--r--r-- 1 root root 4096 Aug 22 13:50 runtime_active_kids
-r--r--r-- 1 root root 4096 Aug 22 13:50 runtime_active_time
-r--r--r-- 1 root root 4096 Aug 22 13:50 runtime_enabled
-r--r--r-- 1 root root 4096 Aug 22 13:50 runtime_status
-r--r--r-- 1 root root 4096 Aug 22 13:50 runtime_suspended_time
-r--r--r-- 1 root root 4096 Aug 22 13:50 runtime_usage[/INDENT]
[INDENT]
# ls -la /sys/devices/platform/INTC1055\:00/power/
total 0
drwxr-xr-x 2 root root    0 Aug 22 13:51 .
drwxr-xr-x 5 root root    0 Aug 22 06:49 ..
-rw-r--r-- 1 root root 4096 Aug 22 13:52 async
-rw-r--r-- 1 root root 4096 Aug 22 13:52 autosuspend_delay_ms
-rw-r--r-- 1 root root 4096 Aug 22 13:52 control
-r--r--r-- 1 root root 4096 Aug 22 13:52 runtime_active_kids
-r--r--r-- 1 root root 4096 Aug 22 13:52 runtime_active_time
-r--r--r-- 1 root root 4096 Aug 22 13:52 runtime_enabled
-r--r--r-- 1 root root 4096 Aug 22 13:52 runtime_status
-r--r--r-- 1 root root 4096 Aug 22 13:52 runtime_suspended_time
-r--r--r-- 1 root root 4096 Aug 22 13:52 runtime_usage
[/INDENT]

The only GPIO the kernel seems to know about on this chip is labeled 'power':

[INDENT]# cat /sys/kernel/debug/gpio
gpiochip0: GPIOs 664-1023, parent: platform/INTC1055:00, INTC1055:00:
 gpio-842 (                    |power               ) in  hi IRQ ACTIVE LOW
[/INDENT]


**After some digging, I've found some more info:**

If I dump /sys/kernel/debug/wakeup_sources before and after a spurious wakeup, I see two counters incrementing:

[INDENT]# cat /sys/kernel/debug/wakeup_sources
name        active_count    event_count    wakeup_count    expire_count    active_since    total_time    max_time    last_change    prevent_suspend_time
gpio-keys.15.auto    1        1        0        0        0        0        0        197704        0
...
PNP0C0D:00      1        1        0        0        0        0        0        204072        0
[/INDENT]

After spurious wakeup:

[INDENT]# cat /sys/kernel/debug/wakeup_sources
name        active_count    event_count    wakeup_count    expire_count    active_since    total_time    max_time    last_change    prevent_suspend_time
gpio-keys.15.auto    2        2        0        0        0        0        0        758632        0
...
PNP0C0D:00      2        2        0        0        0        0        0        761173        0
[/INDENT]

I've tried to disable wakeup on PNP0C0D:00 by:

[INDENT]echo disabled > /sys/bus/acpi/devices/PNP0C0D:00/power/wakeup.
[/INDENT]

This had no impact that I could discern.

I've tried disabling wakeup on the gpio as well by:

[INDENT]echo disabled > /sys/bus/platform/devices/gpio-keys.15.auto/power/wakeup
[/INDENT]

This later one disabled **both **accelerometer and power button. After this change, I can only wake up the laptop by closing and opeing the lid again.

Before you say, I must have a faulty power button, let me state: **the same behavior (on the same machine) doesn't occur under Windows 11**.

My current working hypothesis is that either the BIOS or Linux somehow configures this laptop to report **both** accelerometer and power button evens on the same GPIO, thus resulting in this strange behavior.

Did anyone see anything similar? Is there anything you suggest I look at, logs to submit, experiment to carry out to solve the issue?

Thanks,
Andras

---

