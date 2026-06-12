---
title: "Changing mouse sensitivity and accelleration doesn't work (mousepad)"
date: 2007-05-27
forum: Hardware &amp; Laptops
---

### Post by djvishnu on 2007-05-27
I am trying to increase the sensitivity/acceleration for my (sony vaio) laptop, but the settings in gnome-mouse-properties have no effect!

The change does effect my external usb mouse, but i cant seen to change anything for my mousepad.

Any thoughts on how to do this?

Thank you

---

### Post by Alex-Mcedonia on 2007-05-27
I had the same problem with my thinkpad and I found a solution im not sure but it mite work for you. Here it is:
echo -n 250  > /sys/devices/platform/i8042/serio1/sensitivity

echo -n 120 > /sys/devices/platform/i8042/serio1/speed

try this and try going to this folders and locating the mouse. 
Thats it....:)

---

### Post by djvishnu on 2007-05-27
:( I cannot find any device that sounds like the mousepad - i am posting the contents of /sys/devices/platform, in case someone know what to look for

```
.
./sonypi
./sonypi/driver
./sonypi/bus
./sonypi/subsystem
./sonypi/modalias
./sonypi/power
./sonypi/power/wakeup
./sonypi/power/state
./sonypi/uevent
./dock.0
./dock.0/undock
./dock.0/docked
./dock.0/bus
./dock.0/subsystem
./dock.0/modalias
./dock.0/power
./dock.0/power/wakeup
./dock.0/power/state
./dock.0/uevent
./bluetooth
./bluetooth/bus
./bluetooth/subsystem
./bluetooth/modalias
./bluetooth/power
./bluetooth/power/wakeup
./bluetooth/power/state
./bluetooth/uevent
./iTCO_wdt
./iTCO_wdt/bus
./iTCO_wdt/subsystem
./iTCO_wdt/modalias
./iTCO_wdt/power
./iTCO_wdt/power/wakeup
./iTCO_wdt/power/state
./iTCO_wdt/uevent
./vesafb.0
./vesafb.0/bus
./vesafb.0/subsystem
./vesafb.0/modalias
./vesafb.0/power
./vesafb.0/power/wakeup
./vesafb.0/power/state
./vesafb.0/uevent
./eisa.0
./eisa.0/bus
./eisa.0/subsystem
./eisa.0/modalias
./eisa.0/power
./eisa.0/power/wakeup
./eisa.0/power/state
./eisa.0/uevent
./i8042
./i8042/serio1
./i8042/serio1/resync_time
./i8042/serio1/resetafter
./i8042/serio1/resolution
./i8042/serio1/rate
./i8042/serio1/protocol
./i8042/serio1/input:ts2
./i8042/serio1/input:event3
./i8042/serio1/input:mouse2
./i8042/serio1/input:input3
./i8042/serio1/driver
./i8042/serio1/id
./i8042/serio1/id/extra
./i8042/serio1/id/id
./i8042/serio1/id/proto
./i8042/serio1/id/type
./i8042/serio1/bus
./i8042/serio1/subsystem
./i8042/serio1/bind_mode
./i8042/serio1/drvctl
./i8042/serio1/modalias
./i8042/serio1/description
./i8042/serio1/power
./i8042/serio1/power/wakeup
./i8042/serio1/power/state
./i8042/serio1/uevent
./i8042/serio0
./i8042/serio0/input:event1
./i8042/serio0/id
./i8042/serio0/id/extra
./i8042/serio0/id/id
./i8042/serio0/id/proto
./i8042/serio0/id/type
./i8042/serio0/input:input1
./i8042/serio0/err_count
./i8042/serio0/softraw
./i8042/serio0/softrepeat
./i8042/serio0/set
./i8042/serio0/scroll
./i8042/serio0/extra
./i8042/serio0/driver
./i8042/serio0/bus
./i8042/serio0/subsystem
./i8042/serio0/bind_mode
./i8042/serio0/drvctl
./i8042/serio0/modalias
./i8042/serio0/description
./i8042/serio0/power
./i8042/serio0/power/wakeup
./i8042/serio0/power/state
./i8042/serio0/uevent
./i8042/driver
./i8042/bus
./i8042/subsystem
./i8042/modalias
./i8042/power
./i8042/power/wakeup
./i8042/power/state
./i8042/uevent
./serial8250
./serial8250/driver
./serial8250/tty:ttyS3
./serial8250/tty:ttyS2
./serial8250/tty:ttyS1
./serial8250/tty:ttyS0
./serial8250/bus
./serial8250/subsystem
./serial8250/modalias
./serial8250/power
./serial8250/power/wakeup
./serial8250/power/state
./serial8250/uevent
./pcspkr
./pcspkr/bus
./pcspkr/subsystem
./pcspkr/modalias
./pcspkr/power
./pcspkr/power/wakeup
./pcspkr/power/state
./pcspkr/uevent
./power
./power/wakeup
./power/state
./uevent

```

---

### Post by Alex-Mcedonia on 2007-05-27
try going into the serio1 folder and see if there is a file (not a folder) named speed or sensitivity and tell me what you got

---

### Post by nickpaton on 2007-05-27
have a look at [this]("http://ubuntuforums.org/showthread.php?t=303660") post which worked great for my HP laptop from Dapper to Feisty.

---

### Post by djvishnu on 2007-05-27
serio1 is a directory.. :(

---

### Post by Alex-Mcedonia on 2007-05-27
ok go /sys/devices/platform/i8042/serio1 in here there should be speed sensitivity if there are just open a terminal and as a root type in the comands that i gave you

---

### Post by djvishnu on 2007-05-28
Ok, look at this - here I do a find inside /sys/devices/platform/i8042 as root to see if there is any file/dir called sensitivity or speed, without luck. I also dump and attach the file with all the names if you'd like too have a look :).


```
0 root@vaio:/sys/devices/platform/i8042# find -L 2>/dev/null | grep -i sens
0 root@vaio:/sys/devices/platform/i8042# find -L 2>/dev/null | grep -i speed
0 root@vaio:/sys/devices/platform/i8042# find -L 2>/dev/null > /home/vishnu/sys-dump.txt

```

(I needed 2>/dev/null to supress find's warnings about symlink loops)

Your can also view the attached file at [http://folk.ntnu.no/jornsand/files/sys-dump.txt](http://folk.ntnu.no/jornsand/files/sys-dump.txt)

---

### Post by strabes on 2007-06-13
[http://gentoo-wiki.com/HARDWARE_Synaptics_Touchpad](http://gentoo-wiki.com/HARDWARE_Synaptics_Touchpad)

[http://strabes.wordpress.com/2006/11/04/change-your-touchpad-sensitivity-in-ubuntu/](http://strabes.wordpress.com/2006/11/04/change-your-touchpad-sensitivity-in-ubuntu/)

---

