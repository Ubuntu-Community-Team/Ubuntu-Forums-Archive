---
title: "problem in webcam driver"
date: 2008-11-28
forum: Hardware
---

### Post by shariefbe on 2008-11-28
i installed the new kernel version 2.6.26......in that i selected the module zc0301 as module ie as <m>....but when i inserted the camera the module is installed automatically.....and when i press "dmesg" its showing that the driver is installed.....and when i type "lsmod" the driver zc0301 is there...i dont what happened..but i selected that module as loadable module.....the main thing is my camera is not working..but its in active now..

output of dmesg is:

[  118.644060] usb 2-1: new full speed USB device using uhci_hcd and address 2
[  118.828152] usb 2-1: configuration #1 chosen from 1 choice
[  119.046540] Linux video capture interface: v2.00
[  119.101722] zc0301: V4L2 driver for ZC0301[P] Image Processor and Control Chip v1:1.10
[  119.102437] usb 2-1: ZC0301[P] Image Processor and Control Chip detected (vid/pid 0x041E:0x4034)
[  119.174269] usb 2-1: No supported image sensor detected
[  119.174867] usbcore: registered new interface driver zc0301

output of lsmod is :

sharief@sharief-desktop:~$ lsmod
Module                  Size  Used by
zc0301                 47492  0 
videodev               31232  1 zc0301
v4l1_compat            15364  1 videodev
ipv6                  246500  14 
af_packet              17152  2 
rfcomm                 33808  2 
l2cap                  20352  11 rfcomm
bluetooth              52836  4 rfcomm,l2cap
ppdev                   8196  0 
speedstep_lib           5380  0 
cpufreq_conservative     7432  0 
cpufreq_stats           5952  0 
.
.
.
.
.
.
.
.
.
.


what to do...how to select that module as loadable module..

---

