---
title: "Completely removing/uninstalling built-in webcam."
date: 2009-07-12
forum: Hardware
---

### Post by Soulquarian on 2009-07-12
Hi everyone,

I've very recently installed Ubuntu 9.04 on a laptop and have been trying to familiarise myself with the distro as a total newbie to Linux. What is concerning me is that the built-in webcam on my old-as-the-hills Acer Aspire 3100 (always referred to as an Orbicam on Windows) is permanently turned on - the green LSD is always illuminated.

I had removed the webcam ages ago when still running Windows and wish to do the same now as I don't ever use it. I've searched the forums but most topics regarding webcams seem to be concerned with getting them to work rather than stopping a functional one and I couldn't follow the topics I did find relating to my problem ([http://ubuntuforums.org/showthread.php?t=1057137](http://ubuntuforums.org/showthread.php?t=1057137) and [http://ubuntuforums.org/showthread.php?t=1193131](http://ubuntuforums.org/showthread.php?t=1193131)).

If anybody could help me to completely remove my webcam I'd be very appreciative!

---

### Post by cariboo on 2009-07-12
You should be able to blacklist the driver for your webcam in /etc/modprobe.d/backlist. the problem is to find the correct driver for the device. Open an Applications-->Accessories-->Terminal and type:

```
lsusb
```

the reuslts should look something like this:

```
lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 003: ID 045e:074f Microsoft Corp. 
Bus 002 Device 004: ID 046d:08da Logitech, Inc. QuickCam Messanger
Bus 002 Device 005: ID 0665:5161  
Bus 002 Device 002: ID 045e:00db Microsoft Corp. Natural Ergonomic Keyboard 4000 V1.0
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

In the above example you can see that I have a Logitech Quickcam, and its usb id number is 046d:08da.

To find what driver your webcam uses, in the same terminal type:

```
dmesg | grep 046d:08da
```

Substitute you usb id number for the one in the example above. The results I get when I run the example above look like this:

```
dmesg | grep 046d:08da
[    7.545465] gspca: probing 046d:08da
[    9.600154] gspca: probing 046d:08da
[    9.600166] gspca: probing 046d:08da
[    9.629974] gspca: probing 046d:08da
[    9.629988] gspca: probing 046d:08da
```

In the above example the driver for my device is gspca. To disable the webcam add your driver to the bottom of /etc/modprobe.d/blacklist.

To open the blackist for editing press Alt-F2 and type:

```
gksu gedit /etc/modprobe.d/blacklist
```

Once you add the driver, it won't be loaded on the next reboot.

---

### Post by Soulquarian on 2009-07-12
Thank you very much for the quick reply. I followed all the steps you laid out but, after rebooting, the little green light on the webcam is still on. Just so you can see what I did, here's the contents of my terminal window:

```
lsusb
Bus 001 Device 002: ID 0402:5602 ALi Corp. Video Camera Controller
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
dmesg | grep 0402:5602
[   11.217333] gspca: probing 0402:5602
```After that, I opened the blacklist and it currently reads as follows:

gspca

Do I need to prefix the driver name with something else?

Edit: Of course I do. After a quick search on the forum, file now reads "blacklist gspca" but the thing is STILL on.

---

### Post by xternal5 on 2009-07-30
i got problem using my built-in webcam,any suggestion to solve my problem,i a beginner to ubuntu?..tQ:confused:

xtra5@x5-laptop:~$ lsusb
Bus 002 Device 002: ID 12d1:1003 Huawei Technologies Co., Ltd. E220 HSDPA Modem / E270 HSDPA/HSUPA Modem
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 15d9:0a33  
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 04f2:b026 Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
xtra5@x5-laptop:~$ dmesg | grep 04f2:b026
[   18.284778] uvcvideo: Found UVC 1.00 device Acer Crystal Eye webcam (04f2:b026)
xtra5@x5-laptop:~$

---

### Post by xternal5 on 2010-01-09
solved after installing cheese...sadly now im not ubuntu fan anymore."sticking to other core."

---

### Post by abandoned45623409 on 2013-02-08
[COLOR=#333333]I once had to disable temporarily the built-in webcam in my laptop. He is what I did:[/COLOR]
 
[COLOR=#333333]First, I used following command to list the devices (my built-in webcam happens to be connected via internal USB):[/COLOR]
```
find /sys/ -path "*usb*product*" -exec ls {} \; -exec cat {} \; 2> /dev/null
```[COLOR=#333333]It prints a series of paths and devices associated with the paths - in my case:[/COLOR]```
/sys/devices/pci0000:00/0000:00:1a.0/usb1/product
EHCI Host Controller
/sys/devices/pci0000:00/0000:00:1d.0/usb2/product
EHCI Host Controller
/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/product
HP HD Webcam [Fixed]
/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4:1.0/input/input5/id/productb230/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/product
HP Integrated Module
/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.8/produc
tEMV Smartcard Reader
```[COLOR=#333333]The path I'm looking for is [/COLOR]*/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/product*[COLOR=#333333] - when I run following command as root, the webcam will be disabled (until the next restart):[/COLOR]
```
echo 1 > /sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/remove
```

---

