---
title: "thinkfan appears to be broken in 15.10?"
date: 2015-12-02
forum: Hardware
---

### Post by eriknelson on 2015-12-02
Hi there,

I have a Lenovo T420 and while doing some initial setup and compiling of 15.10, I noticed my cores getting very hot without any fan reaction. I'm pushing 90C where the fan still just remains around 3600rpm. That led me to installing old thinkfan, assuming my fans were not being correctly operated out of the box. However, thinkfan as it's packaged now, does not launch. This is an almost virgin install, and the T420 is a pretty venerable linux box, although the kernel has moved much passed what I used to run on this guy, so maybe something has changed?

Nonetheless, I think this may be a bug with the thinkfan package, or I'm negligently missing a something. I have found a couple similar reports with systemd, but they don't appear to be directly my issue, particularly [https://bugzilla.redhat.com/show_bug.cgi?id=1118961](https://bugzilla.redhat.com/show_bug.cgi?id=1118961)

Systemd output confirms it's not running:

```

&#9679; thinkfan.service - simple and lightweight fan control program
   Loaded: loaded (/lib/systemd/system/thinkfan.service; enabled; vendor preset: enabled)
   Active: failed (Result: exit-code) since Wed 2015-12-02 11:59:58 EST; 2h 15min ago

Dec 02 11:59:58 grimm systemd[1]: Starting simple and lightweight fan control program...
Dec 02 11:59:58 grimm thinkfan[606]: thinkfan 0.9.1 starting...
Dec 02 11:59:58 grimm systemd[1]: thinkfan.service: Control process exited, code=exited status=4
Dec 02 11:59:58 grimm systemd[1]: Failed to start simple and lightweight fan control program.
Dec 02 11:59:58 grimm systemd[1]: thinkfan.service: Unit entered failed state.
Dec 02 11:59:58 grimm systemd[1]: thinkfan.service: Failed with result 'exit-code'.

```

Running in the foreground also fails:

```

WARNING: Using default fan control in /proc/acpi/ibm/fan.

WARNING: Using default temperature inputs in /proc/acpi/ibm/thermal.
/proc/acpi/ibm/thermal: No such file or directory

add_sensor: Error getting temperature.
/proc/acpi/ibm/thermal: No such file or directory

Error parsing temperatures: 
readconfig: Error getting temperature.
Refusing to run without usable config file!

```

Indeed, /proc/acpi/ibm does not yield a thermal file:

```

# ls -lta /proc/acpi/ibm               
total 0
dr-xr-xr-x 2 root root 0 Dec  2 14:28 .
dr-xr-xr-x 4 root root 0 Dec  2 14:28 ..
-rw-r--r-- 1 root root 0 Dec  2 14:28 beep
-rw-r--r-- 1 root root 0 Dec  2 14:28 bluetooth
-rw-r--r-- 1 root root 0 Dec  2 14:28 cmos
-r--r--r-- 1 root root 0 Dec  2 14:28 driver
-rw-r--r-- 1 root root 0 Dec  2 14:28 fan
-rw-r--r-- 1 root root 0 Dec  2 14:28 hotkey
-rw-r--r-- 1 root root 0 Dec  2 14:28 led
-rw-r--r-- 1 root root 0 Dec  2 14:28 light
-rw------- 1 root root 0 Dec  2 14:28 video
-rw-r--r-- 1 root root 0 Dec  2 14:28 volume

```

Additionally of potential relevance:
```

find /sys/devices -type f -name "temp*_input"
/sys/devices/virtual/hwmon/hwmon0/temp1_input
/sys/devices/platform/coretemp.0/hwmon/hwmon2/temp3_input
/sys/devices/platform/coretemp.0/hwmon/hwmon2/temp1_input
/sys/devices/platform/coretemp.0/hwmon/hwmon2/temp2_input

```

I am using the default thinkpad.conf configuration. I'd like to get a second opinion and confirm this is possibly a bug with the package before officially filling. Could someone please advise?

---

