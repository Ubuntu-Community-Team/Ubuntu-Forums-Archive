---
title: "lsusb ifconfig association?"
date: 2009-07-01
forum: Hardware
---

### Post by gurt on 2009-07-01
I'm trying to figure out which device is which. I've got 4 USBs connected to hubs (devices 5,6,8,9). I'm trying to find out what their MAC addrs are. Is there a way to see which device is which eth?

```
gurt@mingus:/etc/udev/rules.d$ lsusb -t
Bus#  1
`-Dev#   1 Vendor 0x1d6b Product 0x0002
  |-Dev#   2 Vendor 0x058f Product 0x6254
  | |-Dev#   5 Vendor 0x0a46 Product 0x9601
  | `-Dev#   6 Vendor 0x0a46 Product 0x0268
  |-Dev#   3 Vendor 0x058f Product 0x6254
  | |-Dev#   8 Vendor 0x0a46 Product 0x0268
  | `-Dev#   9 Vendor 0x0a46 Product 0x9601
  `-Dev#   4 Vendor 0x0ace Product 0x1215
```

```
gurt@mingus:/etc/udev/rules.d$ ifconfig | grep eth
eth0      Link encap:Ethernet  HWaddr 00:e0:4d:8c:d6:e0  
eth1      Link encap:Ethernet  HWaddr 00:02:b3:28:52:2c  
eth2      Link encap:Ethernet  HWaddr 00:02:b3:28:50:7f  
eth3      Link encap:Ethernet  HWaddr 00:02:b3:28:50:80  
eth4      Link encap:Ethernet  HWaddr 00:02:b3:28:52:6a  
eth5      Link encap:Ethernet  HWaddr 00:02:b3:28:52:6b  
eth6      Link encap:Ethernet  HWaddr 00:02:b3:28:52:2d  
eth8      Link encap:Ethernet  HWaddr 00:60:6e:35:8e:a2  
eth9      Link encap:Ethernet  HWaddr 00:60:6e:35:ce:a3  
eth10     Link encap:Ethernet  HWaddr 00:60:6e:92:4a:f4  
eth11     Link encap:Ethernet  HWaddr 00:60:6e:35:fc:a3
```

---

### Post by Ayuthia on 2009-07-01
You might work your way through /sys/class/net.  It will have the eth/wlan devices.  So if you have a wlan0, you can check /sys/class/net/wlan0/device/vendor and /sys/class/net/wlan0/device/device for the vendor/device info that will match up with the lsusb values.

---

### Post by gurt on 2009-07-01
Thanks! 
/sys/class/net/eth8$ less address
seems to give me what I need

So if I were to edit /sys/class/net/eth8/mtu, for instance, that would change the MTU for eth8? or is there an easier way to change these parms? Is there anything else I need to do to get that to work? reboot perhaps?

---

### Post by Ayuthia on 2009-07-01
I was thinking that you can change that in /etc/network/interfaces.  Here is a link that gives some info:
[http://www.ubuntugeek.com/how-to-change-mtu-maximum-transmission-unit-of-network-interface-in-ubuntu-linux.html](http://www.ubuntugeek.com/how-to-change-mtu-maximum-transmission-unit-of-network-interface-in-ubuntu-linux.html)

---

### Post by gurt on 2009-07-01
Dang -- spoke too soon. I actually have that info.
```
/sys/class/net/eth8$ less address
seems to give me what I need
```

I don't seem to have vendor or device info at this level....

```
gurt@mingus:/sys/class/net/eth8/device$ ls -l
total 0
-r--r--r-- 1 root root 4096 2009-07-02 08:18 bAlternateSetting
-r--r--r-- 1 root root 4096 2009-07-02 08:18 bInterfaceClass
-r--r--r-- 1 root root 4096 2009-07-02 08:18 bInterfaceNumber
-r--r--r-- 1 root root 4096 2009-07-02 08:18 bInterfaceProtocol
-r--r--r-- 1 root root 4096 2009-07-02 08:18 bInterfaceSubClass
-r--r--r-- 1 root root 4096 2009-07-02 08:18 bNumEndpoints
lrwxrwxrwx 1 root root    0 2009-07-02 06:56 driver -> ../../../../../../../bus/usb/drivers/dm9601
lrwxrwxrwx 1 root root    0 2009-07-02 08:18 ep_02 -> usb_endpoint/usbdev1.6_ep02
lrwxrwxrwx 1 root root    0 2009-07-02 08:18 ep_81 -> usb_endpoint/usbdev1.6_ep81
lrwxrwxrwx 1 root root    0 2009-07-02 08:18 ep_83 -> usb_endpoint/usbdev1.6_ep83
-r--r--r-- 1 root root 4096 2009-07-02 08:18 modalias
drwxr-xr-x 3 root root    0 2009-07-02 06:56 net
drwxr-xr-x 2 root root    0 2009-07-02 08:18 power
lrwxrwxrwx 1 root root    0 2009-07-02 06:56 subsystem -> ../../../../../../../bus/usb
-r--r--r-- 1 root root 4096 2009-07-02 08:18 supports_autosuspend
-rw-r--r-- 1 root root 4096 2009-07-02 06:56 uevent
drwxr-xr-x 5 root root    0 2009-07-02 06:56 usb_endpoint
```

---

### Post by Ayuthia on 2009-07-01
Have you check the bInterface* information:
```
cat bInter*
```That might provide some information.

I don't have a ethernet card in any of my USB ports so I don't have the exact information, but these are the things that I usually do to find the information that I want.

---

### Post by Ayuthia on 2009-07-01
You might want to check out lshal.  It will give you information about your hardware devices.  You can do a search on net and you should find some information about your network devices.

---

