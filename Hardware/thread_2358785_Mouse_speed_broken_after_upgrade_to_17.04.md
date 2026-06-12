---
title: "Mouse speed broken after upgrade to 17.04"
date: 2017-04-17
forum: Hardware
---

### Post by public-mosteo on 2017-04-17
Hi there,

just upgraded to 17.04 and now my mouse (a plain Logitech USB-PS/2 Optical Mouse) is much slower and nothing I do changes its speed. 

Tried through the settings interface, using xset and using xinput. Nothing seems to do anything. The only thing that offers some feedback is xinput, that complaints about a value out of range:

```
$ xinput --set-prop 8 289 2
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  131 (XInputExtension)
  Minor opcode of failed request:  57 ()
  Value in failed request:  0x121
  Serial number of failed request:  19
  Current serial number in output stream:  20

```

where 8 is the device id, 289 is the "libinput Accel Speed", and 2 is the desired multiplier.

Basically I can set that value to the range 0..1, with no effect, or outside and getting the error. Likewise, changing values with xset shows them as changed, but the mouse is oblivious to it.

Any ideas?

---

### Post by Autodave on 2017-04-17
Did you try simply going into *Settings (gui)* and try that?

---

### Post by rotkiv433 on 2017-04-17
I have the same problem, I tried going in Settings but nothing happens when I lower down the pointer speed. Tried everything in terminal but nothing seems to work. Please help asap, my pointer speed is flying over my desktop.

---

### Post by gqmelo on 2017-04-17
A bug report was open: [https://bugs.launchpad.net/ubuntu/+source/unity-control-center/+bug/1683145](https://bugs.launchpad.net/ubuntu/+source/unity-control-center/+bug/1683145)

---

### Post by public-mosteo on 2017-04-17
Yes, as I said in the first post IIRC, I tried too through the settings interface.

Just now I tried in a live USB (only through the settings gui) and there is no appreciable difference between either slider extrema.

I've gone ahead an reported it in this bug: [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/1683435](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/1683435)

---

