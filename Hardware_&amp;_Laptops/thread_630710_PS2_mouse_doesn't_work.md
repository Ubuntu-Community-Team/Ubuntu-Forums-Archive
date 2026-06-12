---
title: "PS/2 mouse doesn't work"
date: 2007-12-03
forum: Hardware &amp; Laptops
---

### Post by hictio on 2007-12-03
I have installed Ubuntu 7.10 on a Compaq Presario 1200, maxxed the RAM, and swapped the HDD for a 20 GB one I took from a dead iBook. Everything is peachy, except for the PS/w mouse, no matter what I try, I can't get it to work.
The Synapstic touch pad works flawlessly, but the mouse is like dead.

The port and the mouse does work, on the same box I was running FreeBSD, and everything worked, switched to Ubuntu b/c I need the Cisco VPN client.

Here is the relevant info from the /etc/X11/xorg.conf file:

```

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                       "/dev/input/mice"
        Option          "Protocol"                     "ImPS/2"
        Option          "ZAxisMapping"             "4 5"
        Option          "Emulate3Buttons"         "true"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                        "/dev/psaux"
        Option          "Protocol"                      "auto-dev"
        Option          "HorizEdgeScroll"         "0"
EndSection

```

And from the "/proc/bus/input/devices" file:

```

I: Bus=0017 Vendor=0001 Product=0001 Version=0100
N: Name="Macintosh mouse button emulation"
P: Phys=
S: Sysfs=/class/input/input0
U: Uniq=
H: Handlers=mouse0 event0 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3

I: Bus=0011 Vendor=0002 Product=0007 Version=0fa1
N: Name="SynPS/2 Synaptics TouchPad"
P: Phys=isa0060/serio1/input0
S: Sysfs=/class/input/input12
U: Uniq=
H: Handlers=mouse1 event2 
B: EV=b
B: KEY=6420 0 670000 0 0 0 0 0 0 0 0
B: ABS=11000003

```

Any tip on howto make the PS/2 working it is really, really appreciated, as I'm driving completelly crazy with the touchpad.

TIA :D

---

### Post by hictio on 2007-12-03
One thing I forgot to mention, the PS/2 mouse did not work any time, nor during the install. Had to use the touchpad from day one.

---

### Post by indie_design on 2007-12-03
Have you tried using /dev/input/mouse0 as your input device?

Just a guess...

---

### Post by hictio on 2007-12-03
Thanks, I did, to no avail.
No matter what I try, I can't get Ubuntu to use the PS/2 mouse.

---

### Post by indie_design on 2007-12-04
Most mice these days come with a USB<->PS/2 converter... If you can find one of these, you might be able to full ubuntu into using it via USB.

---

### Post by hictio on 2007-12-07
I found the answer, I'll post it in case someone has the same problem.
[ps/2 mouse](https://lists.ubuntu.com/archives/ubuntu-users/2006-August/091809.html)

You have to unload the psmouse kernel module, and remount it, passing it an option.

---

