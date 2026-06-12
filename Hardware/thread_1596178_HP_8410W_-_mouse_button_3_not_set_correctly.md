---
title: "HP 8410W - mouse button 3 not set correctly"
date: 2010-10-14
forum: Hardware
---

### Post by uiberto on 2010-10-14
Hi,

I'm using an HP 8510w.

The middle mouse button registers as a left mouse click. When I run xev, the left and middle button clicks register as "Button 1" and the right button click registers as "Button 3".

```

~$ xinput --list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=10	[slave  pointer  (2)]
&#9116;   &#8627; PS/2 Generic Mouse                      	id=11	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=8	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=9	[slave  keyboard (3)]
    &#8627; HP WMI hotkeys                          	id=12	[slave  keyboard (3)]

```

I then tried playing with "xinput set-button-map" for id 10 and 11 with various button mappings with no effect.

I didn't have this problem on 10.04. I kept my home folder from 10.04, so maybe it's a bogus config file somewhere.

Any ideas?

uiberto

---

### Post by bilderbuchi on 2010-10-14
no ideas, but this affects me, too, on an HP 8530w :(
quite annoying, in fact...

---

### Post by uiberto on 2010-10-15
Any thoughts, anyone? Pretty frustrating & disappointing.

---

### Post by bilderbuchi on 2010-10-15
there's a bug on LP that seems to fit, chime in there: 
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/443284](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/443284)

---

### Post by uiberto on 2010-10-15
My problem is a little different. The middle mouse button is detected and will generate a button event in xev. However, whatever is mapped to the mouse1 button is automatically applied to the mouse3 button.

I'm thinking the problem is at the driver level where the device capabilities are defined. I don't know how to find this sort of information, though.

---

### Post by uiberto on 2010-10-16
1. I have no problems when using an external USB mouse. The middle mouse button functions as expected.

2. This patch did not seem to help. [https://bugs.launchpad.net/udev/+bug/637208/](https://bugs.launchpad.net/udev/+bug/637208/)

3. Here is my xinput get-button-map output (device id's are listed in the original post):
```

$ xinput get-button-map 10
1 2 3 4 5 6 7 8 9 10 11 12 
$ xinput get-button-map 11
1 2 3 4 5 
$ xinput get-button-map 4
1 2 3 4 5 6 7 8 9 10

```

4. This is the output from xev when I press the left button, then the middle button, then the right button.
```

ButtonPress event, serial 33, synthetic NO, window 0x4600001,
    root 0x27a, subw 0x4600002, time 598303, (31,38), root:(531,91),
    state 0x0, button 1, same_screen YES

EnterNotify event, serial 33, synthetic NO, window 0x4600001,
    root 0x27a, subw 0x0, time 598304, (31,38), root:(531,91),
    mode NotifyGrab, detail NotifyInferior, same_screen YES,
    focus YES, state 256

KeymapNotify event, serial 33, synthetic NO, window 0x0,
    keys:  0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

ButtonRelease event, serial 33, synthetic NO, window 0x4600001,
    root 0x27a, subw 0x4600002, time 598388, (31,38), root:(531,91),
    state 0x100, button 1, same_screen YES

LeaveNotify event, serial 33, synthetic NO, window 0x4600001,
    root 0x27a, subw 0x0, time 598388, (31,38), root:(531,91),
    mode NotifyUngrab, detail NotifyInferior, same_screen YES,
    focus YES, state 0

EnterNotify event, serial 33, synthetic NO, window 0x4600001,
    root 0x27a, subw 0x0, time 609248, (31,38), root:(531,91),
    mode NotifyGrab, detail NotifyInferior, same_screen YES,
    focus YES, state 256

KeymapNotify event, serial 33, synthetic NO, window 0x0,
    keys:  122 0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

LeaveNotify event, serial 33, synthetic NO, window 0x4600001,
    root 0x27a, subw 0x0, time 609248, (31,38), root:(531,91),
    mode NotifyUngrab, detail NotifyInferior, same_screen YES,
    focus YES, state 256

ButtonPress event, serial 33, synthetic NO, window 0x4600001,
    root 0x27a, subw 0x4600002, time 609248, (31,38), root:(531,91),
    state 0x0, button 1, same_screen YES

EnterNotify event, serial 33, synthetic NO, window 0x4600001,
    root 0x27a, subw 0x0, time 609248, (31,38), root:(531,91),
    mode NotifyGrab, detail NotifyInferior, same_screen YES,
    focus YES, state 256

KeymapNotify event, serial 33, synthetic NO, window 0x0,
    keys:  122 0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

ButtonRelease event, serial 33, synthetic NO, window 0x4600001,
    root 0x27a, subw 0x4600002, time 609336, (31,38), root:(531,91),
    state 0x100, button 1, same_screen YES

LeaveNotify event, serial 33, synthetic NO, window 0x4600001,
    root 0x27a, subw 0x0, time 609336, (31,38), root:(531,91),
    mode NotifyUngrab, detail NotifyInferior, same_screen YES,
    focus YES, state 0

EnterNotify event, serial 33, synthetic NO, window 0x4600001,
    root 0x27a, subw 0x0, time 611699, (31,38), root:(531,91),
    mode NotifyGrab, detail NotifyInferior, same_screen YES,
    focus YES, state 1024

KeymapNotify event, serial 33, synthetic NO, window 0x0,
    keys:  122 0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

LeaveNotify event, serial 33, synthetic NO, window 0x4600001,
    root 0x27a, subw 0x0, time 611700, (31,38), root:(531,91),
    mode NotifyUngrab, detail NotifyInferior, same_screen YES,
    focus YES, state 1024

ButtonPress event, serial 33, synthetic NO, window 0x4600001,
    root 0x27a, subw 0x4600002, time 611699, (31,38), root:(531,91),
    state 0x0, button 3, same_screen YES

EnterNotify event, serial 33, synthetic NO, window 0x4600001,
    root 0x27a, subw 0x0, time 611700, (31,38), root:(531,91),
    mode NotifyGrab, detail NotifyInferior, same_screen YES,
    focus YES, state 1024

KeymapNotify event, serial 33, synthetic NO, window 0x0,
    keys:  122 0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

ButtonRelease event, serial 33, synthetic NO, window 0x4600001,
    root 0x27a, subw 0x4600002, time 611724, (31,38), root:(531,91),
    state 0x400, button 3, same_screen YES

LeaveNotify event, serial 33, synthetic NO, window 0x4600001,
    root 0x27a, subw 0x0, time 611724, (31,38), root:(531,91),
    mode NotifyUngrab, detail NotifyInferior, same_screen YES,
    focus YES, state 0

```

Any advice? This is pretty frustrating.

---

### Post by uiberto on 2010-10-16
This fixed it ([https://bugs.launchpad.net/ubuntu/+source/linux/+bug/612591):](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/612591):)

```

sudo apt-get install dkms
wget https://bugs.launchpad.net/ubuntu/+source/linux/+bug/582809/+attachment/1675262/+files/psmouse-2.6.35-22-generic-patched.tar.bz2
tar -xjf psmouse-2.6.35-22-generic-patched.tar.bz2
sudo cp -r psmouse-2.6.35-22-generic /usr/src/
sudo dkms add -m psmouse -v 2.6.35-22-generic
sudo dkms build -m psmouse -v 2.6.35-22-generic
sudo dkms install -m psmouse -v 2.6.35-22-generic

```

Then reboot.

---

### Post by bilderbuchi on 2010-10-17
yes you were right, it was another bug. your fixed helped, thanks!

---

