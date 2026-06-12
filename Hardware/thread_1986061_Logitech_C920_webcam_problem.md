---
title: "Logitech C920 webcam problem"
date: 2012-05-24
forum: Hardware
---

### Post by DancingFlames on 2012-05-24
I have a webcam problem (driver?!?). Basically, I have two machines, with different configurations:
1. is a regular notebook, with precise
2. Is a Beagleboard xm, with oneiric ( the issue is reproducible with precise also)

On the first machine the webcam works in cheese and it is well detected. On the second I get a segmentation fault on cheese, and device busy error in gstreamer.

I don't know how should I tackle this issue, really. I need to say also, that on an older kernel (~2.6.x) this camera worked well on the beagleboard. 

Here are some more informations from the two machines:

Machine 1:
#uname -r
3.2.0-24-generic x86_64

# lsusb
Bus 002 Device 004: ID 046d:0821 Logitech, Inc. HD Webcam C910

# dmesg | tail -n4
[ 5778.915776] usb 2-1.2: new high-speed USB device number 4 using ehci_hcd
[ 5779.279637] uvcvideo: Found UVC 1.00 device <unnamed> (046d:0821)
[ 5779.677167] input: UVC Camera (046d:0821) as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.2/input/input12
[ 5779.764864] usbcore: registered new interface driver snd-usb-audio

Machine 2:
# uname -r
3.2.17-x11 armv7l

# lsusb
Bus 001 Device 010: ID 046d:0821 Logitech, Inc.

# dmesg | tail -n8
[  723.812927] usb 1-2.2: new high-speed USB device number 10 using ehci-omap
[  724.202026] usb 1-2.2: New USB device found, idVendor=046d, idProduct=0821
[  724.202087] usb 1-2.2: New USB device strings: Mfr=0, Product=0, SerialNumber=1
[  724.202117] usb 1-2.2: SerialNumber: DA32BFC0
[  724.644012] ALSA sound/usb/mixer.c:846 5:0: cannot get min/max values for control 2 (id 5)
[  724.659942] ALSA sound/usb/mixer.c:846 5:0: cannot get min/max values for control 2 (id 5)
[  724.671173] uvcvideo: Found UVC 1.00 device <unnamed> (046d:0821)
[  724.689117] input: UVC Camera (046d:0821) as /devices/platform/usbhs-omap.0/ehci-omap.0/usb1/1-2/1-2.2/1-2.2:1.2/input/input7

I'm open to suggestions !

---

### Post by zSeries on 2012-06-07
I am no expert but I do tend to mess around  bit when I cant get something working. I would try installing cheese from source. There are some hints on how to do that here [http://ubuntuforums.org/showthread.php?t=1755039](http://ubuntuforums.org/showthread.php?t=1755039). I am interested in using an HD Webcam on Beagleboard for CCTV (I currently use 2 old TV cards and analog cameras with zoneminder in a desktop) so would like to know how you get on.
Good Luck!

---

