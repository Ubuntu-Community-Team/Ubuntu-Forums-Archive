---
title: "Setting up an eGalax Touchscreen"
date: 2008-09-11
forum: General Help
---

### Post by pezmanlou on 2008-09-11
I have a car computer project in progress and use an eGalax touchscreen in the dashboard.  It is almost the working perfectly in Ubuntu 8.04.  I followed these great instructions from the eee user forums on how to get it configured.

[http://forum.eeeuser.com/viewtopic.php?pid=363668]("http://forum.eeeuser.com/viewtopic.php?pid=363668")

My problem is that in the /etc/X11/xorg.conf entry, an event number must be specified and that number changes every reboot.  Sometimes it is event5 or event3 or some other number.

Is there a way to stop the event number from changing?

So far I have found something on udev, but the more I read about it, the less it seems like the correct answer.

---

### Post by nelodvn on 2009-01-08
Did you try to set it as 
Option  "Device"  "events"
instead in the xorg.conf?
It works for me, it automatically detects which event number corresponds to the touch screen.

But if it does not works, you can add a rule to udev to force the touch screen to work with a enventX only, you can set X. I used this way before, but then I set to "events" in the xorg.conf and it works fine for me.

---

### Post by Stamat on 2010-06-08
You just have to run
> cat /proc/bus/input/devices
and find your eGalax device entry. For instance mine is
> I: Bus=0003 Vendor=0eef Product=0001 Version=0210
N: Name="eGalax INC. USB TouchController"
P: Phys=usb-0000:00:0b.1-2.3/input0
S: Sysfs=/devices/pci0000:00/0000:00:0b.1/usb1/1-2/1-2.3/1-2.3:1.0/input/input2
U: Uniq=
H: Handlers=mouse1 event2 
B: EV=1b
B: KEY=401 30000 0 0 0 0
B: ABS=f
B: MSC=10

The replay is late a lot but I hope this helps someone who stumbles upon this page too.

---

### Post by Stamat on 2010-06-08
You just have to run
> cat /proc/bus/input/devices
and find your eGalax device entry. For instance mine is
> I: Bus=0003 Vendor=0eef Product=0001 Version=0210
N: Name="eGalax INC. USB TouchController"
P: Phys=usb-0000:00:0b.1-2.3/input0
S: Sysfs=/devices/pci0000:00/0000:00:0b.1/usb1/1-2/1-2.3/1-2.3:1.0/input/input2
U: Uniq=
H: Handlers=mouse1 event2 
B: EV=1b
B: KEY=401 30000 0 0 0 0
B: ABS=f
B: MSC=10

The replay is late a lot but I hope this helps someone who stumbles upon this page too.

---

