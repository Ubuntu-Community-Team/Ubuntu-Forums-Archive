---
title: "Not getting usb 2.0 speeds"
date: 2009-01-30
forum: Hardware
---

### Post by ShirishAg75 on 2009-01-30
Hi all, 
 I am running linux 2.6.27.9-generic kernel on ubuntu. I have 4 ports on the back of my motherboard and 2 on the motherboard itself. All the devices I am running are using 1.1 speeds only and not 2.0. 

Here is the output of the devices after changing the ports and rebooting the system. 

```

Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 051d:0002 American Power Conversion Uninterruptible Power Supply
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 058f:6387 Alcor Micro Corp. Transcend JetFlash Flash Drive
Bus 001 Device 002: ID 0bc2:3000 Seagate RSS LLC 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

```

Bus 004 Device 005: ID 058f:6387 Alcor Micro Corp. Transcend JetFlash Flash Drive
Bus 004 Device 002: ID 0bc2:3000 Seagate RSS LLC 
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 051d:0002 American Power Conversion Uninterruptible Power Supply
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

and last but not the least. 

```

Bus 004 Device 006: ID 058f:6387 Alcor Micro Corp. Transcend JetFlash Flash Drive
Bus 004 Device 004: ID 0bc2:3000 Seagate RSS LLC 
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 051d:0002 American Power Conversion Uninterruptible Power Supply
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

This is the output of my /etc/fstab as well. 

```

$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=8249aa04-a33e-4d70-abe1-d59537568e6d /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda1
UUID=60569365-731d-4877-bb6f-6e684a68c12b /boot           ext3    relatime        0       2
# /dev/sda3
UUID=9929c56a-14d9-49fd-b207-6f0841d10b2a /home           ext3    relatime        0       2
# /dev/sda5
UUID=dbcf7969-cd1d-40eb-8fd1-a7f2f8827040 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
none    /proc/bus/usb    usbfs    default 0    0    0    0

```

I have couple of questions :-

a. As can be seen the Device ID of the 2.0 root hub doesn't change? Why?

b. Is there anyway (any driver or something) that will get me usb 2.0 speeds on all the devices?

---

### Post by jamesnmandy on 2009-02-20
i am also needing the answer to this

---

### Post by geraldm on 2009-02-21
The USB connections on the back of the motherboard are fixed in hardware.
Some motherboards have mixed 1.1 or 2.0 ports on the back.
If there is an external USB 2.0 hub plugged into a 1.1 hub, it will never get 2.0 speeds.
To get 2.0 speeds, every connection from the motherboard to the 2.0 speed device  needs to be capable of 2.0.

In the first set, bus 001 is 2.0, with 2 devices, which will get 2.0 speeds if the device is also capable of 2.0 speeds.

In the second set, bus 004 is 2.0 speed, with 2 devices which would also get 2.0 speeds if the devices are capable of it.

All of the other USB ports appear to be capable only of 1.1 speed maximum.  No driver can change this.  The only way to get 2.0 speeds is to have a 2.0 capable hub.  There should be documentation on the motherboard to confirm what speeds are available on the board.

best regards,
Gerald

---

### Post by Jisatsu on 2009-06-21
My usb hdd is also slow (1.1)  I know it can run faster, because i used to have Windows XP on the same machine and USB 2.0 was available.  This seems to be a standard issue...

---

### Post by dashxdr on 2010-01-15
I'm not sure if the USB device ID's of the hubs define the USB 1.0 vs USB 2.0 behaviour.

My Asus motherboard has 12 USB ports. 6 come out the connector on the back. All those ports are connected to a Linux Foundation 1.1 root hub (1d6b:0001). Yet I'm sure I've gotten USB 2.0 perforrmance out of some devices pluged into them.

Then on the motherboard there are the pin header strips for connecting more USB ports, but I don't have any of the adapters. All these ports are connected to a Linux Foundation 2.0 root hub (1d6b:0002).

Now my take is that the Linux Foundation 1.1 controller is part of an NVIDIA integrated chipset. Those big SOC devices are hard to manufacture (expensive) so they must be used over a long lifetime. As such the 1.1 controller is probably an older version. Now the 2.0 controller is probably a separate pci device, in a completely separate chip. As such it can be a newer version. That's why there is a mix of Linux Foundation 1.1 and Linux Foundation 2.0.

But I think they're all capable of USB 2.0 performance.
Here's my lsusb with no devices plugged in:

Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Anyway it's all just a theory. Hope this comment is useful. I tried to find what "Linux Foundation" is, but had no luck. Is it some open IP core source? Linux friendly circuits? I don't know...

-Dave

---

### Post by mhampson on 2010-08-03
I am having this same problem of peculiar use of slow 1.1 when 2.0 should be available.

And there appears to be no link between the physical USB socket used and the Bus number allocated!

Here's my Acer Aspire One with nothing connected (the webcam is built in):

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 064e:d101 Suyin Corp. Acer CrystalEye Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Here it is with an a rather excellent USB-to-IDE adapter connecting me to an old internal hard drive taken out of another machine - see how it connects to the only USB 2.0 root hub, Bus 001 (and performs at high speed):

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 008: ID 152d:2337 JMicron Technology Corp. / JMicron USA Technology Corp. 
Bus 001 Device 005: ID 064e:d101 Suyin Corp. Acer CrystalEye Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

...but if I connect the same device to the same physical socket on the laptop via a USB 2.0 hub/splitter, it switches to the lower speed Bus 003, even though the same physical socket on the PC is being used, and the splitter is rated USB 2.0 high speed...

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 017: ID 152d:2337 JMicron Technology Corp. / JMicron USA Technology Corp. 
Bus 003 Device 016: ID 05e3:0606 Genesys Logic, Inc. USB 2.0 Hub / D-Link DUB-H4 USB 2.0 Hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 064e:d101 Suyin Corp. Acer CrystalEye Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

...and you can definitely tell the difference in performance - a 15-fold drop in transfer speeds!

Here, by contrast, iPod happily installs itself on high speed Bus 001 alongside the IDE-connector-without-splitter even though it's connected to the laptop via a different physical socket:

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 011: ID 152d:2337 JMicron Technology Corp. / JMicron USA Technology Corp. 
Bus 001 Device 010: ID 05ac:120a Apple, Inc. iPod Nano
Bus 001 Device 005: ID 064e:d101 Suyin Corp. Acer CrystalEye Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

What's going on?

---

### Post by Fafler on 2010-08-03
In almost any case, the USB 2.0 controller has an integrated USB 1.1 part for legacy USB support. Just ignore it. There doesn't need to be any relationship between which physical port shows up with a specifec bus number, but USB 2.0 devices should inherit the number from the 2.0 root hub. The ECHI controller, if active, will take control of any connected USB 2.0 devices and pass control of USB 1.1 devices to one of the UHCI parts. In short, on most boards except soem very old parts, the USB 2.0 root hub span all physical USB ports and each of the legacy USB 1.1 hubs span two ports each.

My guess is "USB hub changes speed to USB 1.1 issue" could be related to the hub not being powered by an external source. On connect any USB device negotiates speed as well as power consumption and other things with the host port/hub and maybe it needs more than the 500 mA USB is able to deliver to achieve highspeed.

Also, if lsusb shows a USB 2.0 root hub, all needed drives are active and working. Output from lspci | grep USB and the last lines of dmesg after connecting a device are more usefull.

---

### Post by handaxe on 2012-05-17
A dead thread but for the record:

a device attached to a usb 2.0 (high-speed) capable port can be switched to full-speed because of irq issues. This can happen transparently even after attaching as high-speed (syslog will show it).

Attaching ```
pci=routeirq
``` to the boot-options can give greater stability.

---

