---
title: "Webcam not Detected in /dev"
date: 2011-01-18
forum: Hardware
---

### Post by ierosvin on 2011-01-18
Hello,

i have this new laptop. but cant find the built-in camera in /dev/.

i tried the ff:

```
$lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 5986:0241 Acer, Inc 
Bus 001 Device 003: ID 0bda:8189 Realtek Semiconductor Corp. RTL8187B Wireless 802.11g 54Mbps Network Adapter
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```my webcam is being detected correctly as Bus 001 Device 002: ID 5986:0241 Acer, Inc.

also i tried:

```
$lsusb -v
```and i noticed that it is listed in /dev/bus/usb/001/ as 002. i dont know what this means.
i expected the webcam to be listed in /dev as video0.

other info:

```
$lsmod | grep video
uvcvideo               45415  0 
videodev               26099  1 uvcvideo
v4l1_compat            10806  2 uvcvideo,videodev
i2c_core               12093  1 videodev
usbcore                91985  5 rtl8187,uvcvideo,ohci_hcd,ehci_hcd
video                  15391  0 
output                  1224  1 video
thermal_sys             9782  3 thermal,video,processor
```in other systems, we can

```
$cat /dev/video0 > test.jpg
```and this is what im trying to do with my webcam. so that, hopefully, i can access my webcam using IOCTL. :D

help please.

thanks in advance.

---

### Post by IcarusR on 2011-01-18
Try installing cheese, it's in the repositories, & see if your webcam works.

---

### Post by ierosvin on 2011-01-24
but cheese setup needs the /dev/video* too. the problem is i dont have video in my /dev folder.

the site says if video* doesnt exist, i have to press a function key to turn it on. thus, i tried evey functions keys on my keyboard, but no luck. any ideas?

thanks.

---

### Post by gordintoronto on 2011-01-24
What version of Ubuntu? The driver (for some webcams?) got pooched in 10.10.

[http://ubuntuforums.org/showthread.php?p=10391326](http://ubuntuforums.org/showthread.php?p=10391326)

---

