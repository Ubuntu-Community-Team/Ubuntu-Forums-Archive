---
title: "Wireless USB Mouse stopped working"
date: 2009-01-20
forum: Hardware
---

### Post by MicahCarrick on 2009-01-20
Hey y'all.

I've got a Logitech wireless USB mouse I've been using for about a year. Recently it stopped working--unfortunately I'm not sure exactly when but possibly after an update.

The mouse still works in Windows but does NOT work on either of my 2 Ubuntu boxes. Both are Ubuntu 8.10 with kernel 2.6.27-9. A corded logitech USB mouse still works fine--it's only the wireless mouse havivng a problem.

It seemingly "disconnects" immediately after being detected. Here is the output from dmesg when the device is plugged in:

```
[ 1697.092180] usb 4-1: new low speed USB device using uhci_hcd and address 2
[ 1697.269204] usb 4-1: configuration #1 chosen from 1 choice
[ 1697.314774] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.0/usb4/4-1/4-1:1.0/input/input12
[ 1697.356961] input,hidraw1: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:1d.0-1
[ 1699.532354] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.0/usb4/4-1/4-1:1.1/input/input13
[ 1699.562753] input,hiddev96,hidraw2: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1d.0-1
[ 1699.712102] usb 4-1: USB disconnect, address 2
```

The "USB disconnect" is what I typically see only when I unplug the mouse... but now it's happening right after it is detected.

Any ideas?

---

### Post by MicahCarrick on 2009-01-21
Still no luck. I also noticed that when I view the output of: 'xinput list' I see the device popup up immediately after being plugged in:

```
"Logitech USB Receiver"	id=9	[XExtensionPointer]
	Num_buttons is 32
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 1

```

And then it disappears after a few seconds (when I issue 'xinput list' again).

Still no ideas anyone?

---

### Post by MicahCarrick on 2009-01-21
Some more clues from /var/log/Xorg.0.log

```
(II) config/hal: Adding input device Logitech USB Receiver
(**) Logitech USB Receiver: always reports core events
(**) Logitech USB Receiver: Device: "/dev/input/event12"
(II) Logitech USB Receiver: Found x and y relative axes
(II) Logitech USB Receiver: Found 16 mouse buttons
(II) Logitech USB Receiver: Configuring as mouse
(II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: MOUSE)
(**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
(**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(EE) Logitech USB Receiver: Read error: No such device
(II) config/hal: removing device Logitech USB Receiver
(II) Logitech USB Receiver: Close
(II) UnloadModule: "evdev"
```

---

### Post by Asgaroth on 2009-02-21
I got almost the same problem: I can use the mouse for a few minutes after I boot up Ubuntu, but then at a random point it stops working. Strange thing is that I also have a wireless keyboard but it still works.
Anyone got a solution for this? Maybe any ideas?

---

### Post by kutxo on 2009-03-27
I have the same problem. I did a upgrade in 27/03/2009 and in this moment the problem appears. Somebody have a solution?

---

### Post by Velvet_Man on 2009-04-02
I'm also having a problem with a wireless mouse. However, my Logitech wireless mouse and keyboard set I usually use with my desktop work fine on my Ubuntu 8.10 i386 laptop, but the Benq M310 mini wireless mouse with RF USB transmitter that I bought specifically for my laptop won't work properly. The buttons will work to click on things and the scroll wheel works, but it won't move the cursor.

I've tried a few possible solutions posted in other threads on these boards (something involving editing the xorg.conf file) but that didn't work for me.

Anyone have any other suggestions?

---

