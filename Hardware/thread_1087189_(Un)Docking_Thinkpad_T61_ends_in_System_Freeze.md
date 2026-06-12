---
title: "(Un)Docking Thinkpad T61 ends in System Freeze"
date: 2009-03-04
forum: Hardware
---

### Post by NewProggie on 2009-03-04
Hello,

i am using a Thinkpad T61 together with a Thinkpad Advanced Mini Dock on an external Monitor. OS is Ubuntu 8.10 and I am using the prop. Nvidia driver.

Everytime i hit the eject Button to undock the Thinkpad, the whole system freezes and I have to push the power button for five seconds to reboot. I have no idea for what I have to look for to investigate this problem. 
All i can tell is that Ubuntu is able to recognize the state of docking (docked | undocked) correctly.

```

$ udevinfo -a -p /sys/devices/platform/dock.0/

Udevinfo starts with the device specified by the devpath and then
walks up the chain of parent devices. It prints for every device
found, all possible attributes in the udev rules key format.
A rule to match, can be composed by the attributes of the device
and the attributes from one single parent device.

  looking at device '/devices/platform/dock.0':
    KERNEL=="dock.0"
    SUBSYSTEM=="platform"
    DRIVER==""
    ATTR{modalias}=="platform:dock"
    ATTR{docked}=="0"
    ATTR{uid}=="0"
    ATTR{flags}=="0"

  looking at parent device '/devices/platform':
    KERNELS=="platform"
    SUBSYSTEMS==""
    DRIVERS==""


```

Is this a well-known problem? Can somebody give me an advice?

Thanks in advance

---

### Post by utnubuuser on 2009-03-04
I've got no advice for you, but this problem is documented at launchpad.  I had a x31 that had the same problem, but it was fixed some time ago.  8.10 worked great on the x-series. 
Check the Thinkwiki - they're usually up on all the latest with thinkpads.

---

### Post by NewProggie on 2009-03-05
> **utnubuuser said:**
> I've got no advice for you, but this problem is documented at launchpad.  I had a x31 that had the same problem, but it was fixed some time ago.  8.10 worked great on the x-series. 
Check the Thinkwiki - they're usually up on all the latest with thinkpads.

Thanks.
I've already read through the whole thinkwiki and found this here ([http://www.thinkwiki.org/wiki/UltraBase_X6](http://www.thinkwiki.org/wiki/UltraBase_X6)), but it didn't worked for me :-(

---

