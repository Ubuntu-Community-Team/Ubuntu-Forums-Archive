---
title: "USB mouse to laptop"
date: 2008-03-30
forum: Hardware &amp; Laptops
---

### Post by Saadi on 2008-03-30
Hi,

I have connected a wirless USB mouse to my vaio laptop (model  vgn-sz650n), but it doesn't work. any ideas?

no error messages appear.

please help

---

### Post by chewearn on 2008-03-31
After you plugged in the mouse, what do you get for this command:
```
dmesg | tail
```

And:
```
lsusb
```

---

### Post by chirpilittle on 2008-03-31
Is it doing this on linux only? Does it work when connected to another operating system?

---

### Post by Chris_Cr on 2008-04-04
Hi, just googled here after fresh 7.1 on Thinkpad T42
Plugged in USB wireless mouse and am quickly stumped.

```

:~$ dmesg | tail
[   24.696000] [fglrx] max single Inv  = 0
[   24.696000] [fglrx] total      TIM  = 0
[   30.188000] eth1: no IPv6 routers present
[  178.672000] usb 2-1: new low speed USB device using uhci_hcd and address 2
[  178.844000] usb 2-1: configuration #1 chosen from 1 choice
[  179.268000] usbcore: registered new interface driver hiddev
[  179.284000] input: Logitech USB Receiver as /class/input/input8
[  179.288000] input: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:1d.1-1
[  179.288000] usbcore: registered new interface driver usbhid
[  179.288000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
:~$ lsusb
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 046d:c501 Logitech, Inc. Cordless Mouse Receiver
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

```

No input. yes mouse works.
Both TP pointer and touchpad work.

How do I enable setting mouse button scrolling?

Otherwise so far I'm giddy with how easy, quick and good the install was on this laptop.
Getting ready to try some Win32 vboxes.

Thanks all :)

---

### Post by chewearn on 2008-04-04
> **Chris_Cr said:**
> Hi, just googled here after fresh 7.1 on Thinkpad T42
Plugged in USB wireless mouse and am quickly stumped.

```

:~$ dmesg | tail
[   24.696000] [fglrx] max single Inv  = 0
[   24.696000] [fglrx] total      TIM  = 0
[   30.188000] eth1: no IPv6 routers present
[  178.672000] usb 2-1: new low speed USB device using uhci_hcd and address 2
[  178.844000] usb 2-1: configuration #1 chosen from 1 choice
[  179.268000] usbcore: registered new interface driver hiddev
[  179.284000] input: Logitech USB Receiver as /class/input/input8
[  179.288000] input: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:1d.1-1
[  179.288000] usbcore: registered new interface driver usbhid
[  179.288000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
:~$ lsusb
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 046d:c501 Logitech, Inc. Cordless Mouse Receiver
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

```No input. yes mouse works.
Both TP pointer and touchpad work.

How do I enable setting mouse button scrolling?

Otherwise so far I'm giddy with how easy, quick and good the install was on this laptop.
Getting ready to try some Win32 vboxes.

Thanks all :)

The dmesg and lsusb looks ok.  Are you saying the mouse scrollwheel is not working?  But everything else is fine?

---

### Post by Chris_Cr on 2008-04-04
Sorry. I mentioned two problems I guess.
1. USB (dmesg above) mouse doesn't work at all.

2. Thinkpad built-in middle button, would like that to be scroll button. (you hold it down and can scroll with mouse movement)

---

### Post by Chris_Cr on 2008-04-04
HAHA, Never mind, got it working.

I press both 'connect' buttons and it works now. (base reciever and under mouse)

I'm not worried about the middle mouse button really, just curious.

-C

---

