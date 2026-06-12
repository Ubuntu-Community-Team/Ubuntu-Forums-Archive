---
title: "Exotic USB hardware"
date: 2015-01-10
forum: Hardware
---

### Post by tryphon2 on 2015-01-10
I own a server based on a light Debian distribution where I cannot use modprobe command to connect my unrecognized USB device. But my server limitation is not the subject here. I just want to manually bind a driver to my device. For this, I use my computer with Ubuntu 14.04 up to date.

Ok, I can manage this

# rmmod cdc_acm
# sudo su
# echo 1fef 2018 > /sys/bus/usb-serial/drivers/generic/new_id
# hexdump /dev/ttyUSB0

... and raw data are displayed.

But usb-serial/generic is not available on my server.

There is a documented procedure to manually link a driver to a device: [http://lwn.net/Articles/143397/](http://lwn.net/Articles/143397/)
I physically connect my device to a USB port and I release the acm_cdc driver loaded by default but unsuitable :

```
# rmmod cdc_acm
```

In /sys/bus/usb/devices appear two interfaces (my device has two interfaces): 1-1.1:1.0 and 1-1.1:1.1 which are on the bus 1 - hub port 1 : configuration 1 . interfaces 0 and 1.
In /sys/bus/usb/devices/1-1.1:1.0 (and 1-1.1:1.1), there is no (or no more) symbolic link to a directory called 'driver'; which means that it is controlled by any driver.

I then load the driver usbserial I want to use with my device (this driver is perfect for my hardware) :

```
# sudo insmod /lib/modules/3.13.0-43-generic/kernel/drivers/usb/serial/usbserial.ko
```

(# insmod /lib/modules/3.13.0-43-generic/kernel/drivers/usb/serial/usbserial.ko vendor=0x1fef product=0x2018 works of course under Ubuntu, but, again I cannot use it in my server then this solution is rejected)

A folder usbserial appears in /sys/bus/usb/drivers. This directory contains a file 'bind' with write only access right accessible only by root:

```
# sudo su
```

According to the documentation, I can add my interfaces in this file:

```
# echo -n "1-1.1:1.0" > /sys/bus/usb/drivers/usbserial/bind
# echo -n "1-1.1:1.1" > /sys/bus/usb/drivers/usbserial/bind
```

But these commands return:

bash: echo: write error: No such device

The next alternative is not better:

```
# tee /sys/bus/usb/drivers/usbserial/bind <<< 1-1.1:1.0
```

tee: /sys/bus/usb/drivers/usbserial/bind: No device of this type

Before I plugin my USB device :

/sys/bus/usb/devices/
&#9500;&#9472;&#9472; 1-0:1.0 -> ../../../devices/pci0000:00/0000:00:1a.0/usb1/1-0:1.0
&#9500;&#9472;&#9472; 1-1 -> ../../../devices/pci0000:00/0000:00:1a.0/usb1/1-1
&#9500;&#9472;&#9472; 1-1:1.0 -> ../../../devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1:1.0
&#9500;&#9472;&#9472; 2-0:1.0 -> ../../../devices/pci0000:00/0000:00:1d.0/usb2/2-0:1.0
&#9500;&#9472;&#9472; 2-1 -> ../../../devices/pci0000:00/0000:00:1d.0/usb2/2-1
&#9500;&#9472;&#9472; 2-1.1 -> ../../../devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1
&#9500;&#9472;&#9472; 2-1:1.0 -> ../../../devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0
&#9500;&#9472;&#9472; 2-1.1:1.0 -> ../../../devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1:1.0
&#9500;&#9472;&#9472; 2-1.1:1.1 -> ../../../devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1:1.1
&#9500;&#9472;&#9472; 2-1.2 -> ../../../devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2
&#9500;&#9472;&#9472; 2-1.2:1.0 -> ../../../devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.0
&#9500;&#9472;&#9472; usb1 -> ../../../devices/pci0000:00/0000:00:1a.0/usb1
&#9492;&#9472;&#9472; usb2 -> ../../../devices/pci0000:00/0000:00:1d.0/usb2

After my device is plugged :

/sys/bus/usb/devices/
&#9500;&#9472;&#9472; 1-0:1.0 -> ../../../devices/pci0000:00/0000:00:1a.0/usb1/1-0:1.0
&#9500;&#9472;&#9472; 1-1 -> ../../../devices/pci0000:00/0000:00:1a.0/usb1/1-1
&#9500;&#9472;&#9472; 1-1.1 -> ../../../devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.1
&#9500;&#9472;&#9472; 1-1:1.0 -> ../../../devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1:1.0
&#9500;&#9472;&#9472; [COLOR=#ff0000]1-1.1:1.0 -> ../../../devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.1/1-1.1:1.0[/COLOR]
&#9500;&#9472;&#9472; [COLOR=#ff0000]1-1.1:1.1 -> ../../../devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.1/1-1.1:1.1[/COLOR]
&#9500;&#9472;&#9472; 2-0:1.0 -> ../../../devices/pci0000:00/0000:00:1d.0/usb2/2-0:1.0
&#9500;&#9472;&#9472; 2-1 -> ../../../devices/pci0000:00/0000:00:1d.0/usb2/2-1
&#9500;&#9472;&#9472; 2-1.1 -> ../../../devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1
&#9500;&#9472;&#9472; 2-1:1.0 -> ../../../devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0
&#9500;&#9472;&#9472; 2-1.1:1.0 -> ../../../devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1:1.0
&#9500;&#9472;&#9472; 2-1.1:1.1 -> ../../../devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1:1.1
&#9500;&#9472;&#9472; 2-1.2 -> ../../../devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2
&#9500;&#9472;&#9472; 2-1.2:1.0 -> ../../../devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.0
&#9500;&#9472;&#9472; usb1 -> ../../../devices/pci0000:00/0000:00:1a.0/usb1
&#9492;&#9472;&#9472; usb2 -> ../../../devices/pci0000:00/0000:00:1d.0/usb2

 Then 1-1.1:1.0 and 1-1.1:1.1 EXIST. Root user should be able to write in /sys/bus/usb/drivers/usbserial/bind

What is wrong here ?

---

