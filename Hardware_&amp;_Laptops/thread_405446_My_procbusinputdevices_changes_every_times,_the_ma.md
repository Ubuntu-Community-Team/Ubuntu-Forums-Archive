---
title: "My /proc/bus/input/devices changes every times, the machine is reboot"
date: 2007-04-09
forum: Hardware &amp; Laptops
---

### Post by redqueen on 2007-04-09
Every times, I reboot, my Touchpad handlers toggles between event3 and event2

I: Bus=0011 Vendor=0002 Product=0008 Version=7321
N: Name="AlpsPS/2 ALPS GlidePoint"
P: Phys=isa0060/serio4/input0
S: Sysfs=/class/input/input4
H: Handlers=mouse1 event3 ts1  
B: EV=f
B: KEY=420 0 70000 0 0 0 0 0 0 0 0
B: REL=3
B: ABS=1000003

How can I control it?

Thanks

---

### Post by trubblemaker on 2007-04-25
if you find out let me know it will help to solve a suspend-to-ram issue

---

### Post by sisco311 on 2007-04-25
same problem with lirc and my remote
i fix it using the symlink in /dev/input/by-path dir
in my case /dev/input/by-path/pci-0000:04:09.0--event-ir is the appropriate symlink to /dev/input/event*

---

### Post by trubblemaker on 2007-04-25
sorry I didn't quite follow you can you get a little more specific

---

### Post by sisco311 on 2007-04-25
sorry, bad english
i have a tv tuner with a remote control. i need a program called lirc to get my remote control work. i must run lirc with my remote control event as an argument. something like this:
```
lirc -H /dev/input/event2 ...
```
after a reboot my remote event can be changed to event3 and lirc don't work.
so i figured out that is a directory (/dev/input/by-patch) in witch are symbolic links to the events in the /dev/input directory.
example:
```
ls -all /dev/input/by-path/
total 0
drwxr-xr-x 2 root root 140 Apr 25 09:47 .
drwxr-xr-x 4 root root 320 Apr 25 09:47 ..
lrwxrwxrwx 1 root root   9 Apr 25 09:47 pci-0000:00:0b.0-usb-0:3:1.0-event-mouse -> ../event2
lrwxrwxrwx 1 root root   9 Apr 25 09:47 pci-0000:00:0b.0-usb-0:3:1.0-mouse -> ../mouse1
lrwxrwxrwx 1 root root   9 Apr 25 09:47 pci-0000:04:09.0--event-ir -> ../event3
lrwxrwxrwx 1 root root   9 Apr 25 09:47 platform-i8042-serio-0-event-kbd -> ../event1
lrwxrwxrwx 1 root root   9 Apr 25 09:47 platform-pcspkr-event-spkr -> ../event4

```

the symbolic link name is static(don't change after a reboot) and they target is always the same device event.so if i use the command:
```
lirc -H /dev/input/by-path/pci-0000:04:09.0--event-ir ...
```
lirc works perfect because, if the remote control event3 is changing after a reboot to event2 also my symbolic link target is changing to event2

again sorry for my english (and post your issue. maybe i can help you)

---

