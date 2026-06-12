---
title: "Benq DC 1300 as a webcam"
date: 2010-09-21
forum: Hardware
---

### Post by mitja.felicijan on 2010-09-21
I have Benq DC 1300 camera and I would like to use it like a webcam for my side project. But I cant get it to work with my Ubuntu 10.04 installation. The funny thing is that my Logitech camera is working. And when I connected DC 1300 it also worked. But after reboot DC 1300 stopped working. 

dmesg | tail

[13518.400060] usb 5-2: USB disconnect, address 6
[13540.464026] usb 5-2: new full speed USB device using uhci_hcd and address 7
[13540.705176] usb 5-2: configuration #1 chosen from 1 choice
[13540.708314] gspca: probing 04a5:3003
[13540.731082] gspca: probe ok
[13540.731181] gspca: probing 04a5:3003
[13540.866990] gspca: disconnect complete

lsusb

Bus 005 Device 007: ID 04a5:3003 Acer Peripherals Inc. (now BenQ Corp.) Benq Webcam

lsmod | grep gspca

gspca_sunplus          13780  0 
gspca_stv06xx          23274  0 
gspca_zc3xx            45189  0 
gspca_main             21199  3 gspca_sunplus,gspca_stv06xx,gspca_zc3xx
videodev               34361  1 gspca_main

I have no clue how to get it to work. When I try to run xawtv I get this:

This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.32-24-generic)
xinerama 0: 1680x1050+0+0
xinerama 1: 1680x1050+1680+0
WARNING: No DGA direct video mode for this display.
can't open /dev/video0: No such file or directory
v4l-conf had some trouble, trying to continue anyway
v4l2: open /dev/video0: No such file or directory
v4l2: open /dev/video0: No such file or directory
v4l: open /dev/video0: No such file or directory
no video grabber device available

I tried with the other webcam attached but no difference.

Thnx in advance :)

---

