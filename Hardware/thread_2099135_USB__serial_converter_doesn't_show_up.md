---
title: "USB / serial converter doesn't show up"
date: 2012-12-28
forum: Hardware
---

### Post by dargaud on 2012-12-28
Hello all,
I have two different USB to serial converters that normally work, but sometimes they simply stop working and nothing short of a reboot will make them work again.

I always get this error when I replug the device(s):
```
$ tail -f /var/log/syslog
kernel: [116743.620062] usb 6-1: new full-speed USB device number 5 using ohci_hcd
kernel: [116743.789650] pl2303 6-1:1.0: pl2303 converter detected
udevd[22894]: failed to execute '/lib/udev/mtp-probe' 'mtp-probe /sys/devices/pci0000:00/0000:00:13.1/usb6/6-1 6 5': No such file or directory
kernel: [116743.811481] usb 6-1: pl2303 converter now attached to ttyUSB0
kernel: [116743.873337] pl2303 ttyUSB0: pl2303 converter now disconnected from ttyUSB0
kernel: [116743.873352] pl2303 6-1:1.0: device disconnected
kernel: [116744.411021] usb 6-1: usbfs: process 4191 (EMT-2) did not claim interface 0 before use

$ ll /dev/ttyUSB*
ls: cannot access /dev/ttyUSB*: No such file or directory

$ ll /lib/udev/mtp-probe
ls: cannot access /lib/udev/mtp-probe: No such file or directory

$ lsusb
Bus 006 Device 005: ID 067b:2303 Prolific Technology, Inc. PL2303 Serial Port\
...
```

The devices are a Trendnet TU-S9 and a Unitek but they both show up identical. I've also tried "sudo service uvdev restart" to no avail. I don't want to reboot !

---

### Post by Cheesehead on 2012-12-28
When the device is plugged in, the system (perhaps following a udev rule) tries to run the 'mtp-probe' application.

However, you don't seem to have the 'mtp-probe' application installed, so the rule fails, and the mount fails.

mtp-probe is provided by the libmtp-runtime package, which is a dependency of the libmtp9 package, which is in turn a dependency of many audio players link banshee and rhythmbox.

---

### Post by dargaud on 2012-12-29
Then why do those converters work the first time I plug them in but fail after the 2nd time ?

I did remove libmtp-runtime a while ago because it was causing trouble with an Android device, blocking the possibility to mount as mass storage. I just added it back, but no change:
```
kernel: [155131.056138] usb 5-3: new full-speed USB device number 9 using ohci_hcd
kernel: [155131.224425] pl2303 5-3:1.0: pl2303 converter detected
mtp-probe: checking bus 5, device 9: "/sys/devices/pci0000:00/0000:00:13.0/usb5/5-3"
kernel: [155131.246572] usb 5-3: pl2303 converter now attached to ttyUSB0
mtp-probe: bus: 5, device: 9 was not an MTP device
kernel: [155131.317526] pl2303 ttyUSB0: pl2303 converter now disconnected from ttyUSB0
kernel: [155131.317547] pl2303 5-3:1.0: device disconnected
kernel: [155131.840623] usb 5-3: usbfs: process 4191 (EMT-2) did not claim interface 0 before use

```

---

### Post by Cheesehead on 2012-12-31
> **dargaud said:**
> kernel: [155131.246572] usb 5-3: pl2303 converter now attached to ttyUSB0
[COLOR="Red"]mtp-probe: bus: 5, device: 9 was not an MTP device[/COLOR]

The device you are plugging in is not recognized as an MTP device.
Is that just the serial adapter?
Or is that the device at the other end of the serial cable?
What device is it?

Some devices may require a shim.
Some devices are not really MTP.
Some pl2303 adapters, especially cheap ones, are knockoffs (fakes) that lack full functionality.

---

### Post by dargaud on 2012-12-31
After a reboot the USB/serial adapter registers itself as /dev/ttyUSB0 and works again. From the syslog:
```
kernel: [  544.944074] usb 5-3: new full-speed USB device number 2 using ohci_hcd                
mtp-probe: checking bus 5, device 2: "/sys/devices/pci0000:00/0000:00:13.0/usb5/5-3"                 
mtp-probe: bus: 5, device: 2 was not an MTP device                                                   
kernel: [  545.179123] usbcore: registered new interface driver usbserial
kernel: [  545.179166] USB Serial support registered for generic
kernel: [  545.179241] usbcore: registered new interface driver usbserial_generic
kernel: [  545.179246] usbserial: USB Serial Driver core
kernel: [  545.181377] USB Serial support registered for pl2303
kernel: [  545.181461] pl2303 5-3:1.0: pl2303 converter detected
kernel: [  545.202394] usb 5-3: pl2303 converter now attached to ttyUSB0
kernel: [  545.202450] usbcore: registered new interface driver pl2303
kernel: [  545.202456] pl2303: Prolific PL2303 USB to serial adaptor driver

```
So what is it that keeps it from working again after a 1st failure. And about the possibility of it being a fake, I have two of different brands...

---

### Post by Cheesehead on 2013-01-01
Are you asking "Why, after the first failure, does it continue to fail?"
That answer seems self-evident.

From the log you showed, the kernel's perspective is that it does not recognize the MTP device. Of course, the kernel assumes that the serial-USB adapter is working properly.

So you have four possibilities.
1) The kernel and adapter are working properly and the MTP device is not known to the kernel.
2) The kernel and adapter are working properly and the device is not really an MTP-compatible device.
3) The adapter is faulty.
4) Kernel bug.

If you really want a solution, eliminating several of those possibilities is a good first step. For example, it's not difficult to determine if #1 and #2 are true/false, since the devices recognized by the different kernel versions are well documented.

If, however, you just want to know 'why' something does not work (or does not work after initially working or not-working), feel free to pick any of those four reasons. For example, it's surprising how often I help users who inist their device is MTP-compatible...but actually uses some other method.

---

### Post by wub on 2013-02-22
Dargaud,

Thanks for asking your question, I found a no-name usb -> serial device that I'd like to use, but I couldn't figure out how to identify it. 

I have seen something very much like you describe (works once, not twice) with an SD card reader.  One day, instead of "Safely Removing Drive", I used the other option (don't have the menu in front of me) - and I didn't have to reboot when inserting the next card.  How are you disconnecting the device on the end of the cable?  I think I was unmounting the SD card reader (which was built into the system) each time I attempted to properly remove the card inside it.

---

### Post by dargaud on 2013-05-24
I saw that my mobo had an internal serial connector, so I used a 2$ bar with a DB9 to get a serial port on the back. Problem solved.

---

### Post by dennisn77-ameritech on 2014-03-22
I have a device with the Prolific PL2303 chip in it.  I am using Ubuntu Studio (Basically Xubuntu), and this is for a Ham radio application.  The device doesn't even show up unless I go into a terminal and type lsusb.  Looking at the Prolific website, it says there is a driver for Red hat ONLY.

---

### Post by dennisn77-ameritech on 2014-04-06
> **dennisn77-ameritech said:**
> I have a device with the Prolific PL2303 chip in it.  I am using Ubuntu Studio (Basically Xubuntu), and this is for a Ham radio application.  The device doesn't even show up unless I go into a terminal and type lsusb.  Looking at the Prolific website, it says there is a driver for Red hat ONLY.

Turns out the solution was a simple one.  All I had to do was to add my name to the dialout list:

Go into a terminal:
sudo adduser dennis (In my case) dialout 
(Hit enter)
Give password when asked for it.

Exit the terminal.

Log out of Linux.  Log back in.  And you're done.

---

