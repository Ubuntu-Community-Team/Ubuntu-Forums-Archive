---
title: "How do to that Linux load in modules of more than one webcam always at the same order"
date: 2008-09-08
forum: Hardware
---

### Post by Victor Santos on 2008-09-08
I have a little surveillance system working on ubuntu 8.04 (kernel 2.6.24-19 generic) using motion and 3 webcams, but i have been finding a problem.

Sometimes, when the system restart, the order that Linux detects the webcams change and the webcam that before recorded in a folder start to record in another folder because the devices change the order.

Is it possible to correct it?

---

### Post by IntuitiveNipple on 2008-09-08
Here's the best way to deal with video device naming. Create a udev rule similar to this:
```

SUBSYSTEM=="video4linux", BUS=="usb", SYSFS{idVendor}=="054c", SYSFS{idProduct}=="0154", NAME="video5"

```
It is saved as "**/etc/udev/rules.d/25-name-video-devices.rules**" (requires sudo/gksudo privileges to write the file).

Take notice of == being used to ***test*** existing values passed through udev, and = being used to ***assign*** a new value. 

In this case it is tied to a USB device with the PCI ID 054C:0154 (A Sony Playstation EyeToy camera) using a match with idVendor and idProduct. It will be given the name **video5** which will end up as /dev/video5.

See the udev manual page for more details:
```

man udev

```
To identify the values being passed through udev you would run the udevmonitor just before plugging the device in:
```

sudo udevmonitor --environment | tee video-udev.log

```
This command writes the output to screen but also saves it to the file "video-udev.log" since there can sometimes be a lot of output that needs examining carefully to find the correct attributes to use to recognise the device.

Here's an extract of a part of the log that I used in this example:
```

UEVENT[1220172826.231984] add      /devices/pci0000:00/0000:00:1d.1/usb2/2-1 (usb)
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:1d.1/usb2/2-1
SUBSYSTEM=usb
MAJOR=189
MINOR=131
DEVTYPE=usb_device
DEVICE=/proc/bus/usb/002/004
PRODUCT=54c/154/100
TYPE=0/0/0
BUSNUM=002
DEVNUM=004
SEQNUM=3875

...

UEVENT[1220172826.711537] add      /devices/pci0000:00/0000:00:1d.1/usb2/2-1/video4linux/video1 (video4linux)
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:1d.1/usb2/2-1/video4linux/video1
SUBSYSTEM=video4linux
MAJOR=81
MINOR=1
SEQNUM=3879

```
Notice how PRODUCT contains the PCI device ID without leading zeros.

If it is a built-in device that can't be unplugged then you identify the driver that handles it, and unload the driver, then reload it with udevmonitor running. In the case of the EyeToy camera here, the driver is ov51x-jpeg, so (if it were built-in) I'd do:
```

sudo modprobe -r ov51x-jpeg
sudo udevmonitor --environment | tee video-udev.log&
sudo modprobe ov51x-jpeg
fg

```
Now press Ctrl+C to interrupt udevmonitor and return to the command-line.

**Note:** There will be some output as soon as udevmonitor starts but ignore it and go ahead typing the next command even though the input prompt appears to be missing. The "&" at the end of the udevmonitor command puts the process into the background and returns to the command-line immediately.

You should identify unique values for each of the cameras and use three udev rules in the file, one rule to match each camera and assign it a NAME.

---

