---
title: "Silvercrest MK10 wireless set"
date: 2008-04-24
forum: Hardware
---

### Post by JoskeTobben on 2008-04-24
Hi,

I recently purchased a Silvercrest MK10 wireless multimedia keyboard/mouse set (usb). Surprisingly, the keyboard works just fine (didn't test the extra buttons). The problem however is the mouse. It shows no sign of life, although it works in WinXP.

The "sudo cat /dev/input/mouse*" commands only displays input from my regular mouse, nothing from the wireless mouse. When I run "cat /proc/bus/input/devices", I get this output:

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

I: Bus=0003 Vendor=062a Product=0102 Version=0110
N: Name="MOSART Semi. Wireless Keyboard & Mouse"
P: Phys=usb-0000:00:10.2-1/input0
S: Sysfs=/class/input/input1
U: Uniq=
H: Handlers=kbd event1 
B: EV=120003
B: KEY=10000 7 ff87207a c14057ff febeffdf ffefffff ffffffff fffffffe
B: LED=7

I: Bus=0003 Vendor=062a Product=0102 Version=0110
N: Name="MOSART Semi. Wireless Keyboard & Mouse"
P: Phys=usb-0000:00:10.2-1/input1
S: Sysfs=/class/input/input2
U: Uniq=
H: Handlers=kbd mouse1 event2 
B: EV=f
B: KEY=7fff 2c3027 bf004440 0 0 1f1fe3 f80 8837c400 667bfa d971dfed 9e0000 0 0 0
B: REL=143
B: ABS=1 0

*[...]*

```

Any ideas to get this thing to work?

---

### Post by JoskeTobben on 2008-04-27
Anyone? Nothing I can try?

---

### Post by Sully on 2008-09-27
I recently solved a similar problem with a Mosart wireless USB mouse in Ubuntu on an old Thinkpad A21m laptop.  There are three parts to the problem:  figuring out how Ubuntu handles the mouse then editing the /etc/X11/xorg.conf file correctly, then pairing the mouse and the wireless transmitter.

First in a terminal window:

```
 /proc/bus/input/devices 
```

scroll down and find the Mosart Wireless Mouse entry. Under there will be a line like this:

```
 H: Handlers=mouse0 event1 ts0 
```

This is the line that tells you that the wireless mouse is mouse0.  You will need to enter this information in xorg.conf.

Back up your xorg.conf as xorg.conf.original
You will need root:
```
sudo nano /etc/X11/xorg.conf 
```

scroll down to to Section "InputDevice".  My working version looks like this:

```
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        **Option       "Device"         "/dev/input/mouse0"**
        Option          "Protocol"              "IMPS/2"
        Option          "Emulate3Buttons"       "false"
        Option          "EmulateWheel"          "true"
        Option          "EmulateWheelButton"    "2"
        Option          "ZAxisMapping"          "4 5"  
```

Edit your /dev/input line so that it ends with the Handler from above; in my example, it needs to be /dev/input/mouse0.

Save and exit nano.  Then kill the X11 by ctrl-alt-backspace.  It will restart X and you will need to log in.

Then press the blue pairing light/button on the Mosart USB fob transmitter.  Then press the pairing button on the bottom of the mouse.  If the mouse does not work then restart X again see what happens.

Be advised that your other, existing mouse may no longer function after this change.  (It helps to have a trackpoint on my old IBM).  You may need to completely duplicate the "InputDevice" section for a different mouse, however, I don't know if X will let you have two mouse sections.

I found that the steps needed to be done in this order.  However, the mouse may quit working after reboot, if Ubuntu assigns the wireless mouse to a different Handler during autodetection.  This is a pain but fixable via the above steps.

Sully

---

