---
title: "Need a hand with udev rules"
date: 2007-06-27
forum: Hardware &amp; Laptops
---

### Post by Saubazi on 2007-06-27
I have few problems bringing up my media-pc with mythtv.
I have three dvb cards and the problem is that two of them get automatically loaded during boot - the third I have to load the saa7134-dvb module with entry in /etc/modules

Now the problem is that the two other dvb cards seem to switch positions sometimes one is /dev/dvb/adapter0 and sometimes it is the other one. This does not seem to cause problems itself but the main problem is that I have my remote connected to the other one and thus the right IR controller is /dev/input/event2 and at times /dev/input/event3 - so kind of difficult to get lirc to work with correct input device.

For this reason I'd need to define the stuff with udev rules I believe so that the devices would always have the assigned nodes.

Another problem is that the /dev/input/ have only access to the root so I'd also need to have permissions changed.

I'd appreciate if someone could give me a hand with this one...

---

### Post by Austin_KW on 2007-06-28
You may not need udev rules, at least for the lirc device name.
Check for entries in /dev/input/by-path/ and /dev/input/by-id/ and see it it creates a link to the /dev/input/event*. For my config the /dev/input/by-path/* remains fixed.

---

### Post by Saubazi on 2007-06-28
I'll have to see about that - I would not mind getting them properly assigned though...
I am not fully confident my system can cope with the video cards changing in /dev/adapter 
either.

Anyway this is my trial on udev rules:

$ cat /etc/udev/rules.d/10-local.rules 
BUS=="input", SYSFS{name}=="cx88 IR _Hauppauge Nova-T DVB-T", SYMLINK+="remote", MODE="0666"
KERNEL=="event[0-9]",MODE="0666"

At least I achieved /dev/input/event nodes appearing with the appropriate permissions - "remote" symlink was, however, not created...

---

### Post by Saubazi on 2007-06-28
Does not seem to work the way you suggested.
In one boot the device under by-path was /dev/input/by-path/pci-0000:02:08.0--event-
and now /dev/input/by-path/pci-0000:02:08.2--event-

So no joy - it has to be solved with udev rules...

Next trial 

KERNEL=="event*", SYSFS{name}=="cx88 IR _Hauppauge Nova-T DVB-T", SYMLINK+="remote", MODE="0666"


I have $ udevinfo -a -p /sys/class/input/event3

udevinfo starts with the device the node belongs to and then walks up the
device chain, to print for every device found, all possibly useful attributes
in the udev key format.
Only attributes within one device section may be used together in one rule,
to match the device for which the node will be created.

  looking at device '/class/input/input3/event3':
    KERNEL=="event3"
    SUBSYSTEM=="input"
    SYSFS{dev}=="13:67"

  looking at device '/class/input/input3':
    ID=="input3"
    BUS=="input"
    DRIVER==""
    SYSFS{uniq}==""
    SYSFS{phys}=="pci-0000:02:08.2/ir0"
    SYSFS{name}=="cx88 IR _Hauppauge Nova-T DVB-T"

  looking at device '/devices/pci0000:00/0000:00:08.0/0000:02:08.2':
    ID=="0000:02:08.2"
    BUS=="pci"
    DRIVER=="cx88-dvb"
    SYSFS{modalias}=="pci:v000014F1d00008802sv00000070sd00009002bc04sc80i00"
    SYSFS{local_cpus}=="ff"
    SYSFS{irq}=="201"
    SYSFS{class}=="0x048000"
    SYSFS{subsystem_device}=="0x9002"
    SYSFS{subsystem_vendor}=="0x0070"
    SYSFS{device}=="0x8802"
    SYSFS{vendor}=="0x14f1"

  looking at device '/devices/pci0000:00/0000:00:08.0':
    ID=="0000:00:08.0"
    BUS=="pci"
    DRIVER==""
    SYSFS{modalias}=="pci:v000010DEd0000008Bsv00000000sd00000000bc06sc04i00"
    SYSFS{local_cpus}=="ff"
    SYSFS{irq}=="0"
    SYSFS{class}=="0x060400"
    SYSFS{subsystem_device}=="0x0000"
    SYSFS{subsystem_vendor}=="0x0000"
    SYSFS{device}=="0x008b"
    SYSFS{vendor}=="0x10de"

  looking at device '/devices/pci0000:00':
    ID=="pci0000:00"
    BUS==""
    DRIVER==""

---

### Post by Carlos Santiago on 2007-07-17
Have you restart UDEV service?
```
sudo /etc/init.d/udev restart
```

---

