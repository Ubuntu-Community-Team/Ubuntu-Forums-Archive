---
title: "Z-Star Microelectronics Corp. ZC0301 Webcam displaying no image"
date: 2010-08-21
forum: Hardware
---

### Post by fernandoc1 on 2010-08-21
When I plug my Z-Star Microelectronics Corp. ZC0301 Webcam it displays no image.
I already tested this camera on a Windows Virtual Machine, and it is working properly.
However on Linux, it is not working. I tested it on Cheese, AMSN, and the newer google voice and video plugin.
None of them seems to work.
To quicken the process, I'm putting all info that I could get:

lsusb displays:
Bus 004 Device 003: ID 0ac8:301b Z-Star Microelectronics Corp. ZC0301 Webcam

When I connect the device the dmesg shows:
[16472.300030] usb 4-3: new full speed USB device using ohci_hcd and address 3
[16472.466410] usb 4-3: configuration #1 chosen from 1 choice
[16472.479297] Linux video capture interface: v2.00
[16472.483115] gspca: main v2.7.0 registered
[16472.484966] gspca: probing 0ac8:301b
[16474.304936] zc3xx: probe 2wr ov vga 0x0000
[16474.450919] zc3xx: probe 3wr vga 1 0xc400
[16474.708876] zc3xx: probe 3wr vga 2 0x0000
[16474.764868] zc3xx: Sensor UNKNOW_0 force Tas5130
[16474.772976] gspca: probe ok
[16474.773010] usbcore: registered new interface driver zc3xx
[16474.773016] zc3xx: registered

My system info:
uname -a

Linux fernando-desktop 2.6.32-24-generic #41-Ubuntu SMP Thu Aug 19 01:12:52 UTC 2010 i686 GNU/Linux

Do someone have any suggestions to it?

---

### Post by gradinaruvasile on 2010-08-21
Hm. Interesting. I have a 

Z-Star Microelectronics Corp. ZC0305 Webcam

camera and works OOTB in most applications - Cheese, Pidgin, Gmail web interface etc.
The other applications can use it with a little help:
For example skype:

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

Any application can be loaded with this workaround.

A simple test is to launch

gstreamer-properties

either in a terminal or from the alt+f2 launch menu, go to the video tab, set the camera as "pc camera", press test.

PS i use Debian Squeeze, not Ubuntu.

---

### Post by fernandoc1 on 2010-08-21
This can be an bug in the recent Linux releases.
In openSUSE 11.3 this problem is also happening in the same way as it is happening on Ubuntu.

When I plug this camera on a Xubuntu 6.06 I get this output on dmesg:

[17179646.236000] usb 1-2: new full speed USB device using ohci_hcd and address 3
[17179647.124000] Linux video capture interface: v1.00
[17179647.148000] drivers/usb/media/spca5xx/spca5xx-main.c: USB SPCA5XX camera found. Type Vimicro Zc301P 0x301b
[17179648.548000] usbcore: registered new driver spca5xx
[17179648.548000] drivers/usb/media/spca5xx/spca5xx-main.c: spca5xx driver 00.57.08 registered

ubuntu@ubuntu:~$ uname -a
Linux ubuntu 2.6.15-26-386 #1 PREEMPT Thu Aug 3 02:52:00 UTC 2006 i686 GNU/Linux

I'm not able to test the camera on this system, because I can't find a compatible camera viewer for them in these days.
I wish to be able to mount this USB device remotely to see if it is truly working.
By the way, it would be a great feature on Linux, if some pieces of hardware could be shared via network. Is it possible?

---

### Post by gradinaruvasile on 2010-08-23
Dude 6.06 uses an ancient kernel. Since then tons of new drivers were added. Try a newer version.

---

### Post by fernandoc1 on 2010-08-23
I tested on Ubuntu 10.04, and on Xubuntu 6.06.
They differ on what driver they load.
See the posts above

---

