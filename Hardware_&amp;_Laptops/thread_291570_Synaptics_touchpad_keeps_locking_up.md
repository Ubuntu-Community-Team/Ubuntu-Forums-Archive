---
title: "Synaptics touchpad keeps locking up"
date: 2006-11-02
forum: Hardware &amp; Laptops
---

### Post by The Warlock on 2006-11-02
My Synaptics touchpad keeps locking up at odd intervals for a second or two at a time. I hit dmesg and it spat out something looking like this:

```
[ 1077.198663] psmouse.c: TouchPad at isa0060/serio2/input0 lost sync at byte 1
[ 1077.200418] psmouse.c: TouchPad at isa0060/serio2/input0 lost sync at byte 1
[ 1077.202602] psmouse.c: TouchPad at isa0060/serio2/input0 lost sync at byte 1
[ 1077.204483] psmouse.c: TouchPad at isa0060/serio2/input0 lost sync at byte 1
[ 1077.214621] psmouse.c: TouchPad at isa0060/serio2/input0 lost sync at byte 4
[ 1077.214628] psmouse.c: issuing reconnect request

```

How do I fix this? Other than carrying a USB mouse with my laptop wherever I go?

---

### Post by The Warlock on 2006-11-02
bump

---

### Post by tecteun on 2006-11-04
yep, definitely not a feature :P

same problem on my laptop

---

### Post by tecteun on 2006-11-05
> *knocking on wood*
I believe I found the cure:

adding :
[QUOTE]
usbhid
uhci-hcd
ehci-hcd

to /etc/modules fixes the random locking of the touchpad[/QUOTE]

spoke too soon,
it happened again :S

---

### Post by The Warlock on 2006-11-06
> usbhid
uhci-hcd
ehci-hcd

That wouldn't even make sense. My touchpad (and 99% of laptop touchpads) is a PS/2 interface device, not USB.

---

### Post by tecteun on 2006-11-11
> **The Warlock said:**
> That wouldn't even make sense. My touchpad (and 99% of laptop touchpads) is a PS/2 interface device, not USB.

true, but somehow my laptop made me think i fixed it (though it didnt make sense - usb/ps2 - not all things in life have to make sense:P)....

---

### Post by jpyanowski on 2006-11-13
> **The Warlock said:**
> My Synaptics touchpad keeps locking up at odd intervals for a second or two at a time. I hit dmesg and it spat out something looking like this:

```
[ 1077.198663] psmouse.c: TouchPad at isa0060/serio2/input0 lost sync at byte 1
[ 1077.200418] psmouse.c: TouchPad at isa0060/serio2/input0 lost sync at byte 1
[ 1077.202602] psmouse.c: TouchPad at isa0060/serio2/input0 lost sync at byte 1
[ 1077.204483] psmouse.c: TouchPad at isa0060/serio2/input0 lost sync at byte 1
[ 1077.214621] psmouse.c: TouchPad at isa0060/serio2/input0 lost sync at byte 4
[ 1077.214628] psmouse.c: issuing reconnect request

```



How do I fix this? Other than carrying a USB mouse with my laptop wherever I go?

mesg showed this for my HP laptop:

[17179574.696000] mice: PS/2 mouse device common for all mice

So I've never had a problem with Dapper or Edgy. Sorry.:(

---

### Post by enigma_0Z on 2006-11-16
*bump*

Happens to me too. My touchpad *was* working fine until I tried to install the amd64 version of ubuntu.

Once I had ubuntu installed, the touchpad started doing the same thing.

Now, I've switched back to the 386 version, but I still have the same problem.

---

