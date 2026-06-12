---
title: "Chicony USB Integrated Webcam not detected...ASUS X83vb-x2 (N80)"
date: 2015-02-25
forum: Hardware
---

### Post by kevin_byrne2 on 2015-02-25
lsusb does not see it...

lsusb
Bus 002 Device 003: ID 152d:2329 JMicron Technology Corp. / JMicron USA Technology Corp. JM20329 SATA Bridge
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 003: ID 06f2:002b Emine Technology Co. 
Bus 006 Device 005: ID 046d:c404 Logitech, Inc. TrackMan Wheel
Bus 006 Device 004: ID 046e:5500 Behavior Tech. Computer Corp. Portable Keyboard 86+9 keys (Model 6100C US)
Bus 006 Device 002: ID 0451:2046 Texas Instruments, Inc. TUSB2046 Hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

modprobe uvcvideo says...module not enabled.
lsmod 
Module                  Size  Used by
uvcvideo               80885  0 

After manually starting the module, I see this:

lsmod | grep uvcvideo
uvcvideo               80885  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_core         40664  1 uvcvideo
videodev              134688  2 uvcvideo,videobuf2_core


So the camera, which works in Windows and used to work in Ubuntu 12.x, is simply not working in 14.04.  I have searched high and low on the 'net and can't find anything that works.

These are the different hardware codes for my camera:

HardwareID=USB\Vid_04f2&Pid_b028
HardwareID2=USB\Vid_04f2&Pid_b036
HardwareID3=USB\Vid_04f2&Pid_b029
HardwareID4=USB\Vid_04f2&Pid_b071
HardwareID5=USB\Vid_04f2&Pid_b034
HardwareID6=USB\Vid_04f2&Pid_b106
HardwareID7=USB\Vid_04f2&Pid_b141
HardwareID8=USB\Vid_04f2&Pid_b140
HardwareID9=USB\Vid_04f2&Pid_b13a
HardwareID10=USB\Vid_04f2&Pid_b16B
HardwareID11=USB\Vid_04f2&Pid_b16E
HardwareID12=USB\Vid_04f2&Pid_b189

---

