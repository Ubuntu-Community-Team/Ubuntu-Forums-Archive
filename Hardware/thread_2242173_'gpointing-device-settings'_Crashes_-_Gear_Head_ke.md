---
title: "'gpointing-device-settings' Crashes - Gear Head keybd Trackpad issues"
date: 2014-08-31
forum: Hardware
---

### Post by TBerk on 2014-08-31
OK, So, First off:

Ubuntu Studio 14.04 64bit
AMD Dual Core, 2G RAM, HP Desktop.


```
$ xinput --list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; USB Keyboard                            	id=9	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Power Button                            	id=7	[slave  keyboard (3)]
    &#8627; USB Keyboard                            	id=8	[slave  keyboard (3)]
```


```
cat /proc/bus/input/devices

I: Bus=0003 Vendor=04d9 Product=2ba0 Version=0110
N: Name="USB Keyboard"
P: Phys=usb-0000:00:02.0-3/input0
S: Sysfs=/devices/pci0000:00/0000:00:02.0/usb2/2-3/2-3:1.0/input/input5
U: Uniq=
H: Handlers=sysrq kbd event2 
B: PROP=0
B: EV=120013
B: KEY=10000 7 ff9f207a c14057ff febeffdf ffefffff ffffffff fffffffe
B: MSC=10
B: LED=7

I: Bus=0003 Vendor=04d9 Product=2ba0 Version=0110
N: Name="USB Keyboard"
P: Phys=usb-0000:00:02.0-3/input1
S: Sysfs=/devices/pci0000:00/0000:00:02.0/usb2/2-3/2-3:1.1/input/input6
U: Uniq=
H: Handlers=kbd mouse0 event3 
B: PROP=0
B: EV=17
B: KEY=1f0000 0 2000000 39fa d841d001 1e0000 0 0 0
B: REL=103
B: MSC=10

```

_gpointing-device-settings_ is now installed but doesn't run... lets see if I can find the error...  
bah, looks like I neither saved my search results nor the actuall error codes, but it was a segfault.

What I'm hoping for is more control over the trackpad than standard mouse sensitivity.

---

