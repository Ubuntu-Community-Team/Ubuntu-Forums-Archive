---
title: "Alps pointing device"
date: 2011-10-25
forum: Hardware
---

### Post by neonick on 2011-10-25
I installed Ubuntu 11.04 on my Lenovo G555 laptop yesterday and I can't seem to get vertical scrolling on the touch pad to work. I browsed through the forums, but they give answers where I have no idea what to do. I'm a new user and don't know much about linux, and my brother is helping me to get up and started until I can learn more. If anyone can explain step-by-step & help me get vertical scrolling back, that would be much appreciated. Thanks in advance.

---

### Post by SteveDee on 2011-10-25
> **neonick said:**
> ...can't seem to get vertical scrolling on the touch pad to work...

Suggest you install tpconfig (go to Synaptic and search for it).

Once installed, open a terminal and type:-
```

tpconfig -i

```
...which should display touchpad information.

I've never used this program, but if its like synclient you should be able to set scroll with something like:-
```

VertEdgeScroll=1

```

---

### Post by neonick on 2011-10-26
I had to type in sudo tpconfig -i to get the following to pull up:

Found Synaptics Touchpad.
Firmware: 8.96 (multiple-byte mode).
Sensor type: unknown (0).
Geometry: rectangular/landscape/up.
Packets: absolute, 80 packets per second.
Corner taps disabled;        no tap gestures.
Edge motion: none.
Z threshold: 6 of 7.
2 button mode; corner tap is right button click.

Typing in tpconfig -i gives me the following message: Could not open PS/2 Port [/dev/psaux].

I tried going into preferences > mouse > touch pad to enable vertical scrolling, but there's no option.

---

### Post by SteveDee on 2011-10-26
> **neonick said:**
> ...Found Synaptics Touchpad....

OK, so in a terminal type:-
```

synclient -l

```

If this lists current settings, try:-
```

synclient VertEdgeScroll=1

```

If the synclient command is not recognised you may need to install: xserver-xorg-input-synaptics

You can also remove tpconfig.

---

### Post by neonick on 2011-10-27
The system recognized the first code you posted. It listed the current settings, but setting the vertical edge scroll to 1 did not work. As for installing: xserver-xorg-input-synaptics, it says I already have the latest version installed.

---

### Post by neonick on 2011-11-01
Any other ideas?

---

### Post by Victor101 on 2012-02-11
Try the following package :
[http://people.canonical.com/~sforshee/alps-touchpad/psmouse-alps-0.10/psmouse-alps-dkms_0.10_all.deb](http://people.canonical.com/~sforshee/alps-touchpad/psmouse-alps-0.10/psmouse-alps-dkms_0.10_all.deb)

It is supposed to add the support for alps pointing device.

It works for me on my vaio SB with ubuntu 11.10

---

### Post by nowave7 on 2012-02-12
Hey guys,

I'm also trying to enable multi-touch on an Acer Aspire 5536G which I think has an Alps pointing device, even though sudo tpconfig -i reports:

```

Found Synaptics Touchpad.
Firmware: 8.96 (multiple-byte mode).
Sensor type: unknown (0).
Geometry: rectangular/landscape/up.
Packets: absolute, 80 packets per second.
Corner taps disabled;		no tap gestures.
Edge motion: none.
Z threshold: 6 of 7.
2 button mode; corner tap is right button click.

```

But when running synclient it says:

```
Couldn't find synaptics properties. No synaptics driver loaded?
```
This is what is in /proc/bus/input/devices

```

I: Bus=0011 Vendor=0002 Product=0005 Version=0000
N: Name="ImPS/2 Generic Wheel Mouse"
P: Phys=isa0060/serio1/input0
S: Sysfs=/devices/platform/i8042/serio1/input/input8
U: Uniq=
H: Handlers=mouse1 event8 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=103

```

So I'm guessing this is also Alps device, but I could be wrong.
Any ideas? Thanks.

---

