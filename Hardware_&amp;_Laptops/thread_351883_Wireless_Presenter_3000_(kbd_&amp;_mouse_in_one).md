---
title: "Wireless Presenter 3000 (kbd &amp; mouse in one)"
date: 2007-02-02
forum: Hardware &amp; Laptops
---

### Post by steffen on 2007-02-02
I just got a Microsoft Wireless Presenter 3000 off Microsoft (free as in beer;) ). Apparently it works without installing on Windows, but I haven't been able to test, because I don't have Win - and it doesn't work on Ubuntu Edgy (tried three different computers).

The presenter is pretty cool - it's got a timer, a vibrator, a laserpen, a few mouse buttons and a few arrows for moving around - 16 buttons in all (8 buttons in two modes), and I'd love to give it a spin as a remote for my Ubuntu-powered Elisa-running media centre.

When I stick in the USB stick (for wireless connection), dmesg outputs the following:
> [17278045.248000] usb 2-2: new low speed USB device using uhci_hcd and address 11
[17278045.480000] usb 2-2: configuration #1 chosen from 1 choice
[17278045.500000] input: Device USB Device as /class/input/input17
[17278045.500000] input: USB HID v1.11 Keyboard [Device USB Device] on usb-0000:00:1d.1-2
[17278045.528000] input: Device USB Device as /class/input/input18
[17278045.528000] input: USB HID v1.11 Mouse [Device USB Device] on usb-0000:00:1d.1-2

and cat /proc/bus/input/devices gives me
> I: Bus=0003 Vendor=05fe Product=2002 Version=0210
N: Name="Device USB Device"
P: Phys=usb-0000:00:1d.1-2/input1
S: Sysfs=/class/input/input18
H: Handlers=kbd mouse3 event7 ts3 
B: EV=7
B: KEY=30000 0 20000 3878 d801d101 1e0000 0 0 0
B: REL=3

From devices, it looks as if it's both a keyboard and a mouse in one. So I tried installing xvkbd and xbindkeys, and set up a new keyboard in Xorg.conf, but I don't think that should be necessary, considering that I'm easily adding wireless keyboards to the laptops without having to change any configs. Anyway - no luck so far. When I open the Gnome keyboard shortcut manager and try to hit the buttons to see if anything comes up, I get no result.

Does anyone have any pointers on how to get this Presenter up and running?

Thanks in advance for any suggestions!

---

### Post by steffen on 2007-02-11
Turns out the Microsoft Wireless Presenter 3000 that I got off Microsoft through my company as a celebration for the Vista launch doesn't work. What an irony.

---

### Post by TuxCrafter on 2007-02-20
is your hardware broken or does it not work under linux?

---

### Post by steffen on 2007-02-20
> **TuxCrafter said:**
> is your hardware broken or does it not work under linux?

As far as I can see, hardware is broken. The thing didn't come with a driver-CD, and I tried it with a Win XP SP2 at a friend's, without response. The other units that my workmates got work.

---

### Post by mikeyandmary on 2007-06-14
I don't know if you have thrown it out or not but I was given one of these things as a gift and decided to try and get it to work. I found out that you need to press the button on the end of the USB bit and the small round button on the back of the presenter bit at the same time to "sync" the device and receiver. 

Until I did this (which I discovered by guesswork as I couldn't find written anywhere!!!) the device didn't work in either Windows XP or Ubuntu (Feisty)

Hope this helps...
Michael

---

### Post by steffen on 2007-06-14
> **mikeyandmary said:**
> I don't know if you have thrown it out or not but I was given one of these things as a gift and decided to try and get it to work. I found out that you need to press the button on the end of the USB bit and the small round button on the back of the presenter bit at the same time to "sync" the device and receiver. 

Until I did this (which I discovered by guesswork as I couldn't find written anywhere!!!) the device didn't work in either Windows XP or Ubuntu (Feisty)

Hope this helps...
Michael

Yep - that's what I did as well, and it works :) Plug and play

---

