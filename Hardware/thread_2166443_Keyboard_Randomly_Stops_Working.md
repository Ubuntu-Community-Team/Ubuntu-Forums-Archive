---
title: "Keyboard Randomly Stops Working"
date: 2013-08-09
forum: Hardware
---

### Post by Confused Computer User on 2013-08-09
Hi all,

I am going to make my situation as concise as possible. 

I have a Dell Optiplex755 refurbished that I bought recently. I did a clean install of Kubuntu 12.04 64-bit (all updates done) with no other OS on the system.
The issue I am having is that my Sejin IR Wireless Keyboard with Trackball connected to the computer via a PS/2 - USB Dual Adapter stops working.
What is strange is that the integrated trackball still works but the keyboard is useless. I also have a wireless mouse attached via USB if this helps in any way.

The same setup worked flawlessly on a Dell Dimensions3000. The only difference is that the keyboard was connected via a PS/2 interface with no USB adapter.

So far if I unplug and re-plug the USB adapter I get the keyboard working again. But this is not a valid solution and I hope to be able to sort this out in another fashion that won’t require me to physically reset the USB connection ever so often.

Thank you

---

### Post by slw210 on 2013-08-09
If the track ball still works, wouldn't that point to the keyboard being faulty/losing the connection?

---

### Post by Boab1993 on 2013-08-09
It sounds like a definate problem with the usb adapter, given that is the only thing that changes the issue.

Is it a generic type or is it branded?

type to find out your device name if unknown:

 <code> lsusb --d<code>
<code> lsusb <code>

---

### Post by Confused Computer User on 2013-08-09
Hi,

thank you for the quick replies.

@slw210
The keyboard and trackball are all part of the same unit (See Pic). The connection is via IR receptor no different from a remote control, which is why I like it since the batteries last forever with it.

[IMG]http://www.micwil.com/images/gallery/sejin_america_sejin_ir_wireless_keyboard_with_trackball_p1_518x386.jpg[/IMG]


@Boab1993
I'll do what you suggested once I get home. I bought the device at a Dollar store so it's most likely generic.

---

### Post by Boab1993 on 2013-08-09
Its very possible that the drivers for generic devices don't support the device entirely, given the nature of the usb device being quite specfic.

 you can download additional drivers in user firendly manner by downloading 'Jockey' from the software center, however i couldnt tell you what drivers you need if you have no brand, it would just be the generic drivers.

[https://apps.ubuntu.com/cat/applications/precise/jockey-gtk/](https://apps.ubuntu.com/cat/applications/precise/jockey-gtk/)

There are people who are far more experienced in this area on the forum who im sure will help.

Stay vigilant.

---

### Post by Confused Computer User on 2013-08-09
> **Boab1993 said:**
> Its very possible that the drivers for generic devices don't support the device entirely, given the nature of the usb device being quite specfic.

 you can download additional drivers in user firendly manner by downloading 'Jockey' from the software center, however i couldnt tell you what drivers you need if you have no brand, it would just be the generic drivers.

[https://apps.ubuntu.com/cat/applications/precise/jockey-gtk/](https://apps.ubuntu.com/cat/applications/precise/jockey-gtk/)

There are people who are far more experienced in this area on the forum who im sure will help.

Stay vigilant.

Hi,

Thanks again for the support.
So the first thing is the <code> lsusb <code>  output.

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0ac8:301b Z-Star Microelectronics Corp. ZC0301 Webcam
Bus 003 Device 003: ID 046d:c509 Logitech, Inc. Cordless Keyboard & Mouse
Bus 006 Device 002: ID 05a4:9837 Ortek Technology, Inc. 
Bus 006 Device 005: ID 13ba:0017 Unknown PS/2 Keyboard+Mouse Adapter
Bus 006 Device 004: ID 05a4:9862 Ortek Technology, Inc.


The ortek part is a Targus numpad with two usb outputs that I use when crunching numbers.

I'll try to see if it's a keyboard specific thing by taking it out and using a standard Dell USB keyboard for a while. If the same behaviour occurs I would have eliminated the keyboard as a cause.

I'll post back once I know more.

---

### Post by Boab1993 on 2013-08-09
> **Confused Computer User said:**
> 

Bus 006 Device 005: ID 13ba:0017 Unknown PS/2 Keyboard+Mouse Adapter



That should be your USB adapter just by the by.

Keep us posted sir, someone will answer.

---

### Post by VMC on 2013-08-09
I have a wireless keyboard and mouse, and Kubuntu. I'll have to try that out and see if mine works. I haven't messed with it for quite awhile.

---

### Post by VMC on 2013-08-10
I wonder if the two devices are in conflict with each other:
```
[COLOR=#000000]Bus 003 Device 003: ID 046d:c509 Logitech, Inc. Cordless Keyboard & Mouse[/COLOR]
[COLOR=#000000]Bus 006 Device 005: ID 13ba:0017 Unknown PS/2 Keyboard+Mouse Adapter[/COLOR]
```
Both are keyboard devices.

Also I plugged in my wireless keyboard/mouse and it works great. As good if not better than my wired usb keyboard/mouse.

```
 lsusb -d 04fc:05d8Bus 002 Device 002: ID 04fc:05d8 Sunplus Technology Co., Ltd Wireless keyboard/mouse
```

---

### Post by Confused Computer User on 2013-08-16
> **VMC said:**
> I wonder if the two devices are in conflict with each other:
```
[COLOR=#000000]Bus 003 Device 003: ID 046d:c509 Logitech, Inc. Cordless Keyboard & Mouse[/COLOR]
[COLOR=#000000]Bus 006 Device 005: ID 13ba:0017 Unknown PS/2 Keyboard+Mouse Adapter[/COLOR]
```
Both are keyboard devices.

Also I plugged in my wireless keyboard/mouse and it works great. As good if not better than my wired usb keyboard/mouse.

```
 lsusb -d 04fc:05d8Bus 002 Device 002: ID 04fc:05d8 Sunplus Technology Co., Ltd Wireless keyboard/mouse
```

Thank you for the reply.
They don't seem to be in conflict. At least not to the best of my knowledge. I say this based on the fact that using the same equipment on an older Dell computer (running the same linux) did not result in the above mentioned issue.

I have as promised tried a wired USB (Dell) keyboard which has not resulted in the behavior detailed in my original post.

I will attempt to buy a different PS/2 to USB adapter and report with findings.

Cheers

---

### Post by VMC on 2013-08-16
> ...[COLOR=#000000]Sejin IR Wireless Keyboard with Trackball connected to the computer via a PS/2 - USB Dual Adapter ...[/COLOR]

Maybe I'm misinterpreting the statement above, but have you tried to insert the usb wireless receiver into just a USB port.

---

