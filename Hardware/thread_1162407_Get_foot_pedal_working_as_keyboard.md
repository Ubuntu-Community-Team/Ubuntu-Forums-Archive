---
title: "Get foot pedal working as keyboard?"
date: 2009-05-17
forum: Hardware
---

### Post by polygonal on 2009-05-17
have a foot pedal (INFINITY-IN-USB-1, if that's of any interest) that is implemented as a generic HID device, and I would like it to be behave as control and alt keys. This foot pedal does not register itself as keyboard or even joystick, but as a HID device with UsagePage 12, Usage 3. 

If I issue this in the terminal

```
cat /dev/usb/hiddev0
```

(dev/usb/hiddev0 is my pedal), I get raw codes corresponding to my pedal presses. That's a start. I know what those raw code means: in binary, 0001, 0010, 0100 corresponds to each pedal, respectively, and combination of pedal presses sends combination of those binary number, and releases of pedal trigger input of whatever pedal still being pressed (if all pedal is up, 0000 is sent).

How to I get X to listen to dev/usb/hiddev0 and translate the raw codes into maybe a special keycode so that I can map them with xmodmap or something? Do I need to patch the kernel?

---

### Post by labiloute on 2012-12-18
Hi !

Did you figure this out?

We are in exactly the same situation.

Cheers

---

