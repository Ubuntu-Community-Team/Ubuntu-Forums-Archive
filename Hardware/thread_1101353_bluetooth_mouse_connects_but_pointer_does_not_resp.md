---
title: "bluetooth mouse connects but pointer does not respond"
date: 2009-03-20
forum: Hardware
---

### Post by xingmu on 2009-03-20
I have a Logitech Bluetooth Mouse (M/N: M-RCQ142) that connects successfully with my Bluetooth adapter (generic brand, lsusb gives ID 0c10:0000).  According to the kernel reports, the mouse is recognised and setup as an input device.  But the pointer does not respond to any mouse activity (clicking or moving).  If I try to listen to the handler directly ( cat /dev/input/event8 ) and move the mouse, there is no output.

According to everything else I see, this mouse is supposed to work out of the box.  I have tested it with a Mac and it works normally.  But I cannot get it working on Hardy, Intrepid, or the Jaunty Alpha 5. Can anyone help diagnose and solve the problem?


**dmesg | tail**
```

[  970.051055] input: Bluetooth Laser Travel Mouse as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2:1.0/bluetooth/hci0/hci0:0/input9

```

**cat /proc/bus/input/devices**
```

I: Bus=0005 Vendor=046d Product=b008 Version=0314
N: Name="Bluetooth Laser Travel Mouse"
P: Phys=00:1F:81:00:01:00
S: Sysfs=/devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2:1.0/bluetooth/hci0/hci0:0/input9
U: Uniq=00:07:61:DB:C7:DC
H: Handlers=mouse2 event8 
B: EV=17
B: KEY=ff0000 0 0 0 0 0 0 0 0
B: REL=143
B: MSC=10

```

---

### Post by wolog on 2009-06-07
For the record, the culprit seems to be the bluetooth adapter. I've the same lsusb output, and the same behaviour (tested with two bluetooth mouse).
Replacing with another dongle solve the problem.

---

