---
title: "problem with usb mouse and DELL 2007FP monitor after wake up"
date: 2010-03-27
forum: Hardware
---

### Post by RogerTa on 2010-03-27
Hi all,

I have a usb mouse connected to my ubuntu machine through the usb hub on my monitor.  Normally it works just fine.  However, when the monitor goes to sleep and wakes up, the mouse no longer works.

The scenario is like this:

- the computer is in use, mouse works just fine
- step away from the computer for a while.  The monitor goes to sleep due to being idle
- come back to computer and hit some keys on the keyboard.  This wakes up the monitor
- in most cases, the mouse does not wake up.  Does not even seemed powered on, as the red light that usually emanates from it is missing

To get it working again, I need either unplug and replug the mouse into the monitor, or turn the monitor off and then on again.  As mentioned above, it does seeem that in some cases the mouse does come back to life.

Is there some kind of command that I can run that will probe or kick start the mouse?  This would work just fine for me, since I can login in with the keyboard alone and then run the command to re-enable the mouse.

I am running ubuntu 9.10 on a desktop machine.  The monitor is a Dell 2007FP LCD monitor.  The mouse is a generic logitech optical mouse.

Thanks,
Roger

---

### Post by RogerTa on 2010-03-27
Hi all,

When the mouse is working, the list of usb devices is the following (the mouse device is highlighted in red):

```
$ lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 004: ID 046d:c714 Logitech, Inc.
Bus 004 Device 003: ID 046d:c713 Logitech, Inc.
Bus 004 Device 002: ID 046d:0b04 Logitech, Inc.
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
[COLOR="Red"]**Bus 001 Device 016: ID 046d:c00c Logitech, Inc. Optical Wheel Mouse**[/COLOR]
Bus 001 Device 015: ID 0424:2504 Standard Microsystems Corp. USB 2.0 Hub
Bus 001 Device 003: ID 04b4:6830 Cypress Semiconductor Corp. CY7C68300A EZ-USB >
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

$ lsusb -t
/:  Bus 08.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 07.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 06.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 05.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 04.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
    |__ Port 2: Dev 2, If 0, Class=hub, Driver=hub/3p, 12M
        |__ Port 2: Dev 3, If 0, Class=HID, Driver=usbhid, 12M
        |__ Port 3: Dev 4, If 0, Class=HID, Driver=usbhid, 12M
/:  Bus 03.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 02.Port 1: Dev 1, Class=root_hub, Driver=ehci_hcd/6p, 480M
/:  Bus 01.Port 1: Dev 1, Class=root_hub, Driver=ehci_hcd/6p, 480M
    |__ Port 5: Dev 3, If 0, Class=stor., Driver=ums-cypress, 480M
    |__ Port 6: Dev 15, If 0, Class=hub, Driver=hub/4p, 480M
        |__ [COLOR="red"]**Port 2: Dev 16, If 0, Class=HID, Driver=usbhid, 1.5M**[/COLOR]

```

when the mouse is not working, the list of usb devices is the following (lines in red above are missing):

```
$ lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 004: ID 046d:c714 Logitech, Inc.
Bus 004 Device 003: ID 046d:c713 Logitech, Inc.
Bus 004 Device 002: ID 046d:0b04 Logitech, Inc.
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 015: ID 0424:2504 Standard Microsystems Corp. USB 2.0 Hub
Bus 001 Device 003: ID 04b4:6830 Cypress Semiconductor Corp. CY7C68300A EZ-USB >
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

$ lsusb -t
/:  Bus 08.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 07.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 06.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 05.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 04.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
    |__ Port 2: Dev 2, If 0, Class=hub, Driver=hub/3p, 12M
        |__ Port 2: Dev 3, If 0, Class=HID, Driver=usbhid, 12M
        |__ Port 3: Dev 4, If 0, Class=HID, Driver=usbhid, 12M
/:  Bus 03.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 02.Port 1: Dev 1, Class=root_hub, Driver=ehci_hcd/6p, 480M
/:  Bus 01.Port 1: Dev 1, Class=root_hub, Driver=ehci_hcd/6p, 480M
    |__ Port 5: Dev 3, If 0, Class=stor., Driver=ums-cypress, 480M
    |__ Port 6: Dev 15, If 0, Class=hub, Driver=hub/4p, 480M

```

Note that the three logitech devices listed on bus 004 represent my bluetooth logitech keyboard.

I guess device 015 on bus 001 is usb hub built into the monitor.  It does appear in the list after the monitor wakes up, so I wonder of this is a bug in the monitor's hub.

Any help greatly appreciated.  Thanks,

Roger

---

