---
title: "Ongoing Wacom hotplug/suspend issue"
date: 2011-02-12
forum: Hardware
---

### Post by moaxey on 2011-02-12
My wacom tablet (intuos2) works until sleep/hibernate or hotplug when it becomes unresponsive.

It looks from dmesg like it is given a new /dev/input/inputX address each time it is connected/disconnected, however the new input is not visible in /dev/input/ 

Reloading wacom kernel module has no effect.

Here's some of my outputs:

$ xinput --list
&#9121; Virtual core pointer                id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer        id=4	[slave  pointer  (2)]
&#9116;   &#8627; appletouch                        id=11	[slave  pointer  (2)]
&#9116;   &#8627; Wacom Intuos2 9x12 eraser         id=13	[slave  pointer  (2)]
&#9116;   &#8627; Wacom Intuos2 9x12 cursor         id=14	[slave  pointer  (2)]
&#9116;   &#8627; Wacom Intuos2 9x12 stylus         id=15	[slave  pointer  (2)]
&#9123; Virtual core keyboard                 id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard       id=5	[slave  keyboard (3)]
    &#8627; Power Button                      id=6	[slave  keyboard (3)]
    &#8627; Video Bus                         id=7	[slave  keyboard (3)]
    &#8627; Power Button                      id=8	[slave  keyboard (3)]
    &#8627; Sleep Button                      id=9	[slave  keyboard (3)]
    &#8627; Apple Computer Apple Internal Keyboard / Trackpad	id=10	[slave  keyboard (3)]
    &#8627; Apple Computer Apple Internal Keyboard / Trackpad	id=12	[slave  keyboard (3)]


$ lsusb
Bus 005 Device 005: ID 05ac:8205 Apple, Inc. Bluetooth HCI
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 05ac:8240 Apple, Inc. IR Receiver [built-in]
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 004: ID 056a:0043 Wacom Co., Ltd Intuos2 9x12
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 05ac:021a Apple, Inc. Internal Keyboard/Trackpad (ANSI)
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 008: ID 05ac:8501 Apple, Inc. Built-in iSight [Micron]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


$ dmesg | grep [Ww]acom
[   10.915644] input: Wacom Intuos2 9x12 as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.0/input/input9
[   11.520868] usbcore: registered new interface driver wacom
[   11.520871] wacom: v1.52:USB Wacom tablet driver
[ 4524.076229] PM: resume of drv:wacom dev:3-1:1.0 complete after 1610.639 msecs
[ 4669.011800] input: Wacom Intuos2 9x12 as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.0/input/input17
[ 5091.947621] input: Wacom Intuos2 9x12 as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.0/input/input18
[ 5112.449078] usbcore: deregistering interface driver wacom
[ 5115.683629] input: Wacom Intuos2 9x12 as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.0/input/input19
[ 5116.284339] usbcore: registered new interface driver wacom
[ 5116.284346] wacom: v1.52:USB Wacom tablet driver


$ ls -al /dev/input/
total 0
drwxr-xr-x   4 root root    460 2011-02-12 19:04 .
drwxr-xr-x  20 root root   3900 2011-02-12 18:55 ..
drwxr-xr-x   2 root root    140 2011-02-12 19:04 by-id
drwxr-xr-x   2 root root    180 2011-02-12 19:04 by-path
crw-r-----   1 root root 13, 64 2011-02-11 23:45 event0
crw-r-----   1 root root 13, 65 2011-02-11 23:45 event1
crw-r-----   1 root root 13, 74 2011-02-11 23:45 event10
crw-r-----   1 root root 13, 75 2011-02-11 23:45 event11
crw-rw----+  1 root root 13, 76 2011-02-11 23:45 event12
crw-rw----+  1 root root 13, 77 2011-02-11 23:45 event13
crw-rw----+  1 root root 13, 78 2011-02-11 23:45 event14
crw-r-----   1 root root 13, 66 2011-02-11 23:45 event2
crw-r-----   1 root root 13, 67 2011-02-11 23:45 event3
crw-r-----   1 root root 13, 68 2011-02-11 23:45 event4
crw-r-----   1 root root 13, 69 2011-02-11 23:45 event5
crw-r-----   1 root root 13, 70 2011-02-12 19:04 event6
crw-r-----   1 root root 13, 72 2011-02-11 23:45 event8
crw-r--r--   1 root root 13,  0 2011-02-11 23:45 js0
crw-r-----   1 root root 13, 63 2011-02-11 23:45 mice
crw-r-----   1 root root 13, 32 2011-02-12 19:04 mouse0
crw-r-----   1 root root 13, 34 2011-02-11 23:45 mouse2
lrwxrwxrwx   1 root root      6 2011-02-12 19:04 tablet-intuos2-9x12 -> event6
lrwxrwxrwx   1 root root      6 2011-02-12 19:04 wacom -> event6

I've been stuck on this for a while, help appreciated! :)

---

### Post by moaxey on 2011-02-25
It was the kernel module after all.

The correct way to have the system unload the module before sleep/hibernate and reload it after, is to put a shell script into:

/etc/pm/sleep.d/75_wacom

which senses the sleep events, and issues the module load/unload commands:
```

#!/bin/sh

# load and unload wacom module for suspend and hibernate

case "$1" in
	thaw|resume)
	        modprobe wacom
		;;
	suspend|hibernate)
	        modprobe -r wacom
		;;
esac

```

and of course make it executable
```

 sudo chmod +x /etc/pm/sleep.d/75_wacom

```

However this doesn't fix the hotplug problem!

---

### Post by ohoservices on 2013-03-07
> **moaxey said:**
> It was the kernel module after all.
The correct way to have the system unload the module before sleep/hibernate and reload it after, is to [...]
However this doesn't fix the hotplug problem!

Thx, helped me with Wacom Intuos2 and Ubuntu 12.04 (the problem ist still here).
As for the hotplug for me it works fine the first time.
If I then unplug and try to hotplug again it doesn't work; I have to plug it in, suspend, resume, then ... it works :-)

---

### Post by QIII on 2013-03-07
This is a very old thread.

Closed

---

