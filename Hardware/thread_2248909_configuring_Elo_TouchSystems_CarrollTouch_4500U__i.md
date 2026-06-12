---
title: "configuring Elo TouchSystems CarrollTouch 4500U  in Ubuntu 12.04"
date: 2014-10-18
forum: Hardware
---

### Post by itzbipin on 2014-10-18
Hello All,

We are trying to configure Elo TouchSystems - CarrollTouch 4500U monitor in Ubuntu with the Elo driver . Downloaded the required driver Version 3.5.2-1 from elotouch.com website and installed as per the instruction. In the first installation the driver will install properly and everything works fine. But once the machine is rebooted the driver is getting auto restarted again and again .I can see in the logs that

cat EloUsbErrorLog.txt

```
Found Elo USB Smartset Touchscreen device(s). Device Count:[1]  Max devices:[1]
Could not get Serial Number String for device 0: length[-7]
USB Device 0 not initialized. Restarting driver.
```

Not able to find out a specific reason for this. The only difference i spotted was in  cat /proc/bus/input/devices the below entry is missing when the driver is in properly working condition.


```
I: Bus=0003 Vendor=04e7 Product=0030 Version=0100
N: Name="Elo TouchSystems, Inc. Elo TouchSystems CarrollTouch 4500U"
P: Phys=usb-0000:01:04.1-1.1/input0
S: Sysfs=/devices/pci0000:00/0000:00:1e.0/0000:01:04.1/usb3/3-1/3-1.1/3-1.1:1.0/input/input3
U: Uniq=08A06902
H: Handlers=mouse0 event3 js0
B: PROP=0
B: EV=1b
B: KEY=10000 0 0 0 0 0 0 0 0
B: ABS=100 3
B: MS
```

Tried by removing the default driver usbhid from memory with modprode . In this case the above entry will go but the result is still the same the driver is getting restarted in every 2 sec . Seems like a driver conflict issue or the hardware is not recognized by the kernel but not able to confirm . I’m stuck with on this from the past few days. If anyone having a solution or suggestion  for this issue your help will be highly appreciated  .
Thanks in advance!

---

### Post by Brandon_Jeanpierre on 2015-09-21
I'm having the exact same problem right now and have run into a wall. Did you ever get this issue resolved? if so, how?

---

