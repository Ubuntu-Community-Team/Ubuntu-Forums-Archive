---
title: "need help with ACPI patch for fan control (IBM T43"
date: 2008-10-12
forum: Hardware
---

### Post by Lord Xeb on 2008-10-12
Kernel: 2.6.24-21-generic

okay, i am trying to figure out how to patch my ACPI so that I can have control over my fan. Here is what I have done so far:

```
root@nathan-laptop:/# cd /home/nathan/Desktop
root@nathan-laptop:/home/nathan/Desktop#  patch -p0 -l < thinkpad-acpi.patch
can't find file to patch at input line 5
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|diff --git a/Documentation/leds-class.txt b/Documentation/leds-class.txt
|index 8c35c04..18860ad 100644
|--- a/Documentation/leds-class.txt
|+++ b/Documentation/leds-class.txt
--------------------------
File to patch: /proc/acpi
patch: **** File /proc/acpi is not a regular file -- can't patch
root@nathan-laptop:/home/nathan/Desktop#  patch -p0 -l < thinkpad-acpi.patch
can't find file to patch at input line 5
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|diff --git a/Documentation/leds-class.txt b/Documentation/leds-class.txt
|index 8c35c04..18860ad 100644
|--- a/Documentation/leds-class.txt
|+++ b/Documentation/leds-class.txt
--------------------------
File to patch: /proc/acpi/ibm/fan
patching file /proc/acpi/ibm/fan
Hunk #1 FAILED at 19.
Hunk #2 FAILED at 45.
Hunk #3 FAILED at 82.
patch: **** Can't rename file /proc/acpi/ibm/fan to /proc/acpi/ibm/fan.orig : No such file or directory
root@nathan-laptop:/home/nathan/Desktop#  patch -p0 -l < thinkpad-acpi.patch
can't find file to patch at input line 5
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|diff --git a/Documentation/leds-class.txt b/Documentation/leds-class.txt
|index 8c35c04..18860ad 100644
|--- a/Documentation/leds-class.txt
|+++ b/Documentation/leds-class.txt
--------------------------
File to patch: /proc/acpi/ibm
patch: **** File /proc/acpi/ibm is not a regular file -- can't patch
root@nathan-laptop:/home/nathan/Desktop#  patch -p0 -l < thinkpad-acpi.patch
can't find file to patch at input line 5
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|diff --git a/Documentation/leds-class.txt b/Documentation/leds-class.txt
|index 8c35c04..18860ad 100644
|--- a/Documentation/leds-class.txt
|+++ b/Documentation/leds-class.txt
--------------------------
File to patch: /proc/acpi/fan  
patch: **** File /proc/acpi/fan is not a regular file -- can't patch
root@nathan-laptop:/home/nathan/Desktop# echo level 7 > /proc/acpi/ibm/fan
root@nathan-laptop:/home/nathan/Desktop# cat /proc/acpi/ibm/fan
status:        enabled
speed:        4001
level:        auto
commands:    level <level> (<level> is 0-7, auto, disengaged, full-speed)
commands:    enable, disable
commands:    watchdog <timeout> (<timeout> is 0 (off), 1-120 (seconds))
root@nathan-laptop:/home/nathan/Desktop# echo level 7 > /proc/acpi/ibm/fan
root@nathan-laptop:/home/nathan/Desktop# echo level full-speed > /proc/acpi/ibm/fan
root@nathan-laptop:/home/nathan/Desktop# echo level full-speed > /proc/acpi/ibm/thermal
bash: echo: write error: Input/output error
root@nathan-laptop:/home/nathan/Desktop# echo level 7 > /proc/acpi/ibm/thermalbash: echo: write error: Input/output error
root@nathan-laptop:/home/nathan/Desktop#  patch -p0 -l < thinkpad-acpi.patchcan't find file to patch at input line 5
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|diff --git a/Documentation/leds-class.txt b/Documentation/leds-class.txt
|index 8c35c04..18860ad 100644
|--- a/Documentation/leds-class.txt
|+++ b/Documentation/leds-class.txt
--------------------------
File to patch: /proc/acpi/ibm/fan
patching file /proc/acpi/ibm/fan
Hunk #1 FAILED at 19.
Hunk #2 FAILED at 45.
Hunk #3 FAILED at 82.
patch: **** Can't rename file /proc/acpi/ibm/fan to /proc/acpi/ibm/fan.orig : No such file or directory
root@nathan-laptop:/home/nathan/Desktop#  patch -p0 -l < thinkpad-acpi.patch
can't find file to patch at input line 5
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|diff --git a/Documentation/leds-class.txt b/Documentation/leds-class.txt
|index 8c35c04..18860ad 100644
|--- a/Documentation/leds-class.txt
|+++ b/Documentation/leds-class.txt
--------------------------
File to patch: /proc/acpi/fan
patch: **** File /proc/acpi/fan is not a regular file -- can't patch
root@nathan-laptop:/home/nathan/Desktop#  patch -p0 -l < thinkpad-acpi.patch
can't find file to patch at input line 5
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|diff --git a/Documentation/leds-class.txt b/Documentation/leds-class.txt
|index 8c35c04..18860ad 100644
|--- a/Documentation/leds-class.txt
|+++ b/Documentation/leds-class.txt
--------------------------
File to patch: /proc/acpi/ibm/termal
/proc/acpi/ibm/termal: No such file or directory
Skip this patch? [y] y
Skipping patch.
3 out of 3 hunks ignored
can't find file to patch at input line 70
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|diff --git a/Documentation/rfkill.txt b/Documentation/rfkill.txt
|dissimilarity index 69%
|index a83ff23..0843ed0 100644
|--- a/Documentation/rfkill.txt
|+++ b/Documentation/rfkill.txt
--------------------------
File to patch: /proc/acpi/ibm/thermal
patching file /proc/acpi/ibm/thermal
Hunk #1 FAILED at 1.
patch: **** Can't rename file /proc/acpi/ibm/thermal to /proc/acpi/ibm/thermal.orig : No such file or directory
root@nathan-laptop:/home/nathan/Desktop#  patch -p0 -l < thinkpad-acpi.patch
can't find file to patch at input line 5
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|diff --git a/Documentation/leds-class.txt b/Documentation/leds-class.txt
|index 8c35c04..18860ad 100644
|--- a/Documentation/leds-class.txt
|+++ b/Documentation/leds-class.txt
--------------------------
File to patch: /proc/acpi/ibm/driver
patching file /proc/acpi/ibm/driver
Hunk #1 FAILED at 19.
Hunk #2 FAILED at 45.
Hunk #3 FAILED at 82.
patch: **** Can't rename file /proc/acpi/ibm/driver to /proc/acpi/ibm/driver.orig : No such file or directory
root@nathan-laptop:/home/nathan/Desktop#  patch -p0 -l < thinkpad-acpi.patch
can't find file to patch at input line 5
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|diff --git a/Documentation/leds-class.txt b/Documentation/leds-class.txt
|index 8c35c04..18860ad 100644
|--- a/Documentation/leds-class.txt
|+++ b/Documentation/leds-class.txt
--------------------------
File to patch: --dry-run
--dry-run: No such file or directory
Skip this patch? [y] n
File to patch: /proc/acpi/ib,
/proc/acpi/ib,: No such file or directory
Skip this patch? [y] y
Skipping patch.
3 out of 3 hunks ignored
can't find file to patch at input line 70
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|diff --git a/Documentation/rfkill.txt b/Documentation/rfkill.txt
|dissimilarity index 69%
|index a83ff23..0843ed0 100644
|--- a/Documentation/rfkill.txt
|+++ b/Documentation/rfkill.txt
--------------------------
File to patch: /proc/acpi/ibm
patch: **** File /proc/acpi/ibm is not a regular file -- can't patch
root@nathan-laptop:/home/nathan/Desktop# 

```

What am I doing wrong?

Here are the files in ACPI:

```
root@nathan-laptop:/proc/acpi# ls -l
total 0
dr-xr-xr-x 3 root root 0 2008-10-12 21:03 ac_adapter
-rw-r--r-- 1 root root 0 2008-10-12 21:03 alarm
dr-xr-xr-x 3 root root 0 2008-10-12 20:51 battery
dr-xr-xr-x 5 root root 0 2008-10-12 21:03 button
-r-------- 1 root root 0 2008-10-12 21:03 dsdt
dr-xr-xr-x 3 root root 0 2008-10-12 20:53 embedded_controller
-r-------- 1 root root 0 2008-10-12 16:31 event
-r-------- 1 root root 0 2008-10-12 21:03 fadt
dr-xr-xr-x 2 root root 0 2008-10-12 21:03 fan
dr-xr-xr-x 2 root root 0 2008-10-12 21:03 ibm
-r--r--r-- 1 root root 0 2008-10-12 21:03 info
dr-xr-xr-x 3 root root 0 2008-10-12 20:51 power_resource
dr-xr-xr-x 3 root root 0 2008-10-12 20:51 processor
-rw-r--r-- 1 root root 0 2008-10-12 21:03 sleep
dr-xr-xr-x 3 root root 0 2008-10-12 20:51 thermal_zone
dr-xr-xr-x 3 root root 0 2008-10-12 20:51 video
-rw-r--r-- 1 root root 0 2008-10-12 21:03 wakeup

```

This is inside of IBM:

```
root@nathan-laptop:/proc/acpi/ibm# ls -l
total 0
-rw-r--r-- 1 root root 0 2008-10-12 21:04 beep
-rw-r--r-- 1 root root 0 2008-10-12 21:04 brightness
-rw-r--r-- 1 root root 0 2008-10-12 21:04 cmos
-rw-r--r-- 1 root root 0 2008-10-12 21:04 driver
-rw-r--r-- 1 root root 0 2008-10-12 21:04 fan
-rw-r--r-- 1 root root 0 2008-10-12 21:04 hotkey
-rw-r--r-- 1 root root 0 2008-10-12 21:04 led
-rw-r--r-- 1 root root 0 2008-10-12 21:04 light
-rw-r--r-- 1 root root 0 2008-10-12 21:04 thermal
-rw-r--r-- 1 root root 0 2008-10-12 21:04 video
-rw-r--r-- 1 root root 0 2008-10-12 21:04 volume

```


what do I patch? (patch is in attachments)

---

### Post by overdrank on 2008-10-12
Thread closed duplicate [[COLOR="DarkRed"]Here[/COLOR]](http://ubuntuforums.org/showthread.php?t=945968)
Please do not create multiple threads on the same issue.

---

