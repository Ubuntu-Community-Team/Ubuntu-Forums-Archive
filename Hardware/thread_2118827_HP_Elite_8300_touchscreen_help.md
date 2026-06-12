---
title: "HP Elite 8300 touchscreen help"
date: 2013-02-22
forum: Hardware
---

### Post by tdeboeser on 2013-02-22
Hi,
  I've been googling, but I haven't found a solution for getting the touchscreen to work.  The threads I found are close but it seems 12.10 won't use the drivers.  

The closest solution is:
[http://ubuntuforums.org/showthread.php?t=1898634&page=5](http://ubuntuforums.org/showthread.php?t=1898634&page=5)

But the respository is now 404 and the driver won't install, I get this error:

```

(Reading database ... 143651 files and directories currently installed.)
Unpacking nwfermi (from nwfermi-0.6.5.0_i386.deb) ...
dpkg: dependency problems prevent configuration of nwfermi:
 nwfermi depends on make.
 nwfermi depends on sed (>> 3.0).
 nwfermi depends on dkms.
 nwfermi depends on linux-libc-dev.
 nwfermi depends on libc6-dev.
 nwfermi depends on xf86-input-nextwindow.

dpkg: error processing nwfermi (--install):
 dependency problems - leaving unconfigured
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Errors were encountered while processing:
 nwfermi

```

I've tried to install the dependencies, but they don't install because they are the latest versions. It looks like maybe Ubuntu 11.x may have worked. 

I'm looking for anyone who may have gotten the "multitouch" to work on this system.  The screen is a "NextWindow", Intel graphics card.  

Some info:

lsusb:
```

Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 05af:0802 Jing-Mold Enterprise Co., Ltd 
Bus 001 Device 004: ID 0603:8b03 Novatek Microelectronics Corp. 
Bus 002 Device 003: ID 1926:1846 NextWindow 

```

xinput:
```

&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; ImPS/2 Generic Wheel Mouse              	id=11	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Power Button                            	id=7	[slave  keyboard (3)]
    &#8627;   USB Keyboard                          	id=8	[slave  keyboard (3)]
    &#8627;   USB Keyboard                          	id=9	[slave  keyboard (3)]
    &#8627; UVC Camera (0603:8b03)                  	id=10	[slave  keyboard (3)]
    &#8627; HP WMI hotkeys                          	id=12	[slave  keyboard (3)]

```

dmesg snippit:
```

[    1.744746] usb 2-1.6: >Manufacturer: NextWindow
[    1.746766] hid-generic 0003:1926:1846.0003: >hiddev0,hidraw2: USB HID v1.11 Device [NextWindow Touchscreen] on usb-0000:00:1d.0-1.6/input1

```

Other than the touch screen not working, everything else works normally.

thanks for any tips,

Tomde

---

### Post by tdeboeser on 2013-02-25
No one has one of these systems or has used the nwfermi driver? 

sad face :sad:

---

### Post by justanswering on 2013-02-27
> **tdeboeser said:**
> No one has one of these systems or has used the nwfermi driver? 

sad face :sad:

We just got a bunch of 8300's and had trouble finding the driver deb (the nwfermi ppa repo is still down).

Use the newest one from here:

[https://launchpad.net/nwfermi/+download](https://launchpad.net/nwfermi/+download)

Otherwise the instructions you linked seem to work, thanks a million!

---

### Post by tdeboeser on 2013-03-12
> **justanswering said:**
> We just got a bunch of 8300's and had trouble finding the driver deb (the nwfermi ppa repo is still down).

Use the newest one from here:

[https://launchpad.net/nwfermi/+download](https://launchpad.net/nwfermi/+download)

Otherwise the instructions you linked seem to work, thanks a million!

What? Wait!  You got the driver installed?  Could you elaborate? I've tried the "newest driver" with the same results.  What version of ubuntu?  What changes did you do different from the install above?

Thanks,
Tom

---

