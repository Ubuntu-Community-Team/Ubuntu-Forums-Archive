---
title: "Kernel/device drivers help"
date: 2008-10-24
forum: General Help
---

### Post by Offramp on 2008-10-24
Hi all,

As mentioned over in Beginners Talk I have been trying to sort out a problem with a DVB tuner. The problem was that the device ID was not the same as listed elsewhere.  I found a solution to that problem by rebuilding the v4l-dvb from linuxtv.org with my device id(after reading heaps of posts, bug reports etc!). I plugged the device in and was excited to see that I was a step closer:

> 
dvb-usb: found a 'ASUS My Cinema U3000 Mini DVBT Tuner' in cold state, will try to load a firmware 
/build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: timeout initializing reports 
input: ASUS  U3000 as /devices/pci0000:00/0000:00:1d.7/usb7/7-2/7-2:1.1/input/input15
input,hiddev96,hidraw2: USB HID v1.11 Keyboard [ASUS  U3000 ] on usb-0000:00:1d.7-2

however, the problem now seems to be a conflict with USB HID?  My research begins yet again, but I thought that someone here might be able to help! I suspect that I need to remove the device ID from the hid-core.h file, but I am not sure?

---

