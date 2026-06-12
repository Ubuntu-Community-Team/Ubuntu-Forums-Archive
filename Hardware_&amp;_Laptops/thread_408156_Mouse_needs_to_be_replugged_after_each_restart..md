---
title: "Mouse needs to be replugged after each restart."
date: 2007-04-13
forum: Hardware &amp; Laptops
---

### Post by Schalken on 2007-04-13
Ever since I upgraded to Feisty, my mouse has not worked after starting up. I can click and everything, just the cursor wont move. Once it did budge about 200px while flailing my mouse around. If I unplug it and plug it back in again it works fine, but it is very annoying needing to do this every time I start it up.

If there is no simple answer I will file a bug report.

---

### Post by volksolwagen57 on 2007-04-14
what? is it a usb mouse?

---

### Post by eyelessfade on 2007-04-14
hm. I might have this problem. When I say might ist because I havn't rebootet and testet yet. But as of last upgrade my mouse started acting funny. I had no control of its movement. But when I unpluget it and put it back again it worked. The mouse is a Logitec G7.

output from dmesg:
[  931.928300] usb 7-6.3: new low speed USB device using ehci_hcd and address 6
[  932.022304] usb 7-6.3: configuration #1 chosen from 1 choice
[  932.024052] input: HID 062a:0001 as /class/input/input8
[  932.024124] input: USB HID v1.10 Mouse [HID 062a:0001] on usb-0000:00:1d.7-6.3
[  967.824818] PPP generic driver version 2.4.2
[  969.850555] PPP BSD Compression module registered
[  969.895972] PPP Deflate Compression module registered
[ 1266.047911] usb 4-1: USB disconnect, address 3
[ 1272.411593] usb 4-1: new full speed USB device using uhci_hcd and address 4
[ 1272.598535] usb 4-1: configuration #1 chosen from 1 choice
[ 1272.606538] input: Logitech USB Receiver as /class/input/input9
[ 1272.606592] input: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:1d.1-1
[ 1272.614525] input: Logitech USB Receiver as /class/input/input10
[ 1272.614567] input,hiddev96: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1d.1-1

---

### Post by Schalken on 2007-04-22
Yes it is a Microsoft Intellimouse Optical connected via USB. What seems to have fixed it is connecting it to one of the USB ports on the front, but once I connect it to one of the back ones I have to replug it on each boot. Weird.

---

### Post by Schalken on 2007-04-24
Now sometimes I do have to replug it on the front.

---

### Post by bartman on 2007-04-25
I have started experiencing the same problems with my Logitech mouse. It just stays in the middle of the display until i replug it. Fortunately I'm on a laptop so access is no problem but it is utterly unnecessary.

Have any of you followed any guides to enable extra buttons on your mouse? I can only think of the udev rule I have which might be the cause. My USB keyboard, however, works fine.

---

### Post by Schalken on 2007-04-27
Are you able to click (eg, right-click) while the cursor is stuck in the middle of the screen?

---

### Post by bartman on 2007-04-27
I've solved my problem by reconfiguring the X server and adding an option "DevPhys" to the custom mouse settings.

Now it works without repluging but I think the option that made this possible binds the mouse to a specific USB port.

---

### Post by Cauda_Draconis on 2007-05-01
My mouse keeps getting stuck in the corner or along the left side when my laptop wakes from hibernating and possibly suspend. I can click anywhere on the screen, but the picture of the cursor stays stuck. I have to reboot to make it work properly again.
Anyone know how to fix this?

---

