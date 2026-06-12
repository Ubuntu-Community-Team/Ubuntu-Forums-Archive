---
title: "How to find out &quot;sys device path&quot; for hid2hci?"
date: 2010-12-09
forum: Hardware
---

### Post by sahnemann on 2010-12-09
Hello everyone,

I'm using a Logitech MX900 mouse with Ubuntu 10.10. The mouse doesn't work when I boot the pc, I have to replug it. I found people saying that I need to run hid2hci on the device, but hid2hci keeps telling me I need to provide the "sys device path". I know this is a link to the mouse's bluetooth usb station (which is connected to my PC) somewhere in /sys/, probably /sys/bus/usb/devices/, but I just can't figure out what exactly hid2hci needs as a parameter for --devpath. I tried LOTS of different things, including --devpath=/sys/bus/usb/devices/3-1.1\:1.0/input/input5 but I did not get it to work.

Any help is greatly appreciated.

---

### Post by Myshkin100 on 2011-01-06
I'm trying to get this device working as a bluetooth reciever as well.  So far, I think you can do

lshal

look for the logitech device 'Elite Keyboard Y-RP20 + Mouse MX900 (Bluetooth)'

then look for the linux.sysfs_path (like '/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.5/2-1.5.1')

then remove the /sys from the front.

so:

sudo /lib/udev/hid2hci  --method=logitech-hid --devpath=/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.5/2-1.5.1


Currently mine is giving the error:
error: switching device '/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.5/2-1.5.1' failed.

but that is a step farther than the 'could not find <dev>' message.

---

### Post by Myshkin100 on 2011-01-06
After running through strace, this is the last thing that seems to have gone wrong...


open("/dev/bus/usb/002/008", O_RDWR|O_LARGEFILE) = 3
ioctl(3, HIDIOCINITREPORT, 0)           = -1 ENOTTY (Inappropriate ioctl for device)
close(3)                                = 0

---

