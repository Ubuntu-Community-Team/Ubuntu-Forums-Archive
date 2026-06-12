---
title: "Can't configure my mouse in gutsy"
date: 2007-12-19
forum: Hardware &amp; Laptops
---

### Post by karesz on 2007-12-19
Hi! I hope someone could help me in configuring my mouse! I've searched a lot, but i wasn't able to figure out how to get all buttons, and all wheels working.

I have an A4Tech NB-90 battery-free wireless mouse (working exactly the same as NB-95), which i really like, so i don't want to get an other. I've read through a lot of guides but nothing.

This is my xorg.conf mouse section:

Section "InputDevice"
   Identifier     "Configured Mouse"
   Driver         "mouse"
   Option         "CorePointer"
   Option         "Device" "/dev/input/mice" 
   Option         "Protocol" "ExplorerPS/2"
   Option         "ZAxisMapping" "4 5"
   Option         "Emulate3Buttons" "true"
   Option         "Buttons" "7" 
   Option         "ButtonMapping" "1 2 3 6 7"
EndSection

With this, i am able to use the back and forth buttons, the left, right and middle button, and the wheel properly. What i cant use, is the second wheel, and the 6th button.

cat /proc/bus/input/devices:

I: Bus=0003 Vendor=09da Product=022b Version=0110
N: Name="A4Tech Wireless Battery Free Optical Mouse"
P: Phys=usb-0000:00:1f.2-2/input0
S: Sysfs=/class/input/input3
U: Uniq=
H: Handlers=mouse1 event3 
B: EV=7
B: KEY=ff0000 0 0 0 0 0 0 0 0
B: REL=303


xev shows this:Left button:
ButtonPress event, serial 27, synthetic NO, window 0x3400001,
    root 0x187, subw 0x0, time 4058884636, (97,35), root:(160,409),
    state 0x10, button 1, same_screen YES

ButtonRelease event, serial 27, synthetic NO, window 0x3400001,
    root 0x187, subw 0x0, time 4058884762, (97,35), root:(160,409),
    state 0x110, button 1, same_screen YES

Middle button:
ButtonPress event, serial 30, synthetic NO, window 0x3400001,
    root 0x187, subw 0x0, time 4058984327, (92,94), root:(155,468),
    state 0x10, button 2, same_screen YES

ButtonRelease event, serial 30, synthetic NO, window 0x3400001,
    root 0x187, subw 0x0, time 4058984487, (92,94), root:(155,468),
    state 0x210, button 2, same_screen YES

Right button:
ButtonPress event, serial 30, synthetic NO, window 0x3400001,
    root 0x187, subw 0x0, time 4058985906, (92,94), root:(155,468),
    state 0x10, button 3, same_screen YES

ButtonRelease event, serial 30, synthetic NO, window 0x3400001,
    root 0x187, subw 0x0, time 4058986031, (92,94), root:(155,468),
    state 0x410, button 3, same_screen YES

Back/left side button:
ButtonPress event, serial 30, synthetic NO, window 0x3400001,
    root 0x187, subw 0x0, time 4058987175, (92,94), root:(155,468),
    state 0x10, button 6, same_screen YES

ButtonRelease event, serial 30, synthetic NO, window 0x3400001,
    root 0x187, subw 0x0, time 4058987359, (92,94), root:(155,468),
    state 0x10, button 6, same_screen YES

Forth/right side button:
ButtonPress event, serial 30, synthetic NO, window 0x3400001,
    root 0x187, subw 0x0, time 4058988318, (92,94), root:(155,468),
    state 0x10, button 7, same_screen YES

ButtonRelease event, serial 30, synthetic NO, window 0x3400001,
    root 0x187, subw 0x0, time 4058988494, (92,94), root:(155,468),
    state 0x10, button 7, same_screen YES

6th button:
ButtonPress event, serial 27, synthetic NO, window 0x3400001,
    root 0x187, subw 0x0, time 4059199975, (69,147), root:(74,196),
    state 0x10, button 2, same_screen YES

ButtonRelease event, serial 27, synthetic NO, window 0x3400001,
    root 0x187, subw 0x0, time 4059200159, (69,147), root:(74,196),
    state 0x210, button 2, same_screen YES

first wheel:
ButtonPress event, serial 27, synthetic NO, window 0x3400001,
    root 0x187, subw 0x0, time 4059273023, (155,158), root:(160,207),
    state 0x10, button 5, same_screen YES

ButtonRelease event, serial 27, synthetic NO, window 0x3400001,
    root 0x187, subw 0x0, time 4059273023, (155,158), root:(160,207),
    state 0x1010, button 5, same_screen YES

ButtonPress event, serial 27, synthetic NO, window 0x3400001,
    root 0x187, subw 0x0, time 4059276439, (155,158), root:(160,207),
    state 0x10, button 4, same_screen YES

ButtonRelease event, serial 27, synthetic NO, window 0x3400001,
    root 0x187, subw 0x0, time 4059276439, (155,158), root:(160,207),
    state 0x810, button 4, same_screen YES

second wheel exactly the same...

I've tried to change to evdev, but the X tried to start 3 times, then a 640*480 or 800*600 resolution safe mode jumped up, and then crashes. The keyboard useless, writing arabian and sanskrit characters on the screen.


I'm using gutsy, on a PIII 1ghz 256 mb rd-ram and this mouse on usb

THX in advance!

---

### Post by daou on 2007-12-19
You can try btnx: [http://ubuntuforums.org/showthread.php?t=455656](http://ubuntuforums.org/showthread.php?t=455656)
btnx homepage: [http://www.ollisalonen.com/btnx](http://www.ollisalonen.com/btnx)

Note that you might need to change a few values in your xorg.conf file. That is described in the btnx manual's troubleshooting section (links at the thread).

---

### Post by karesz on 2007-12-19
Thx.
I've tried btnx. btnx haven't installed from deb, compiled, working. btnx-config installed from deb. When i'm rolling the side wheel, it's saying, the button is already detected. But i'll keep trying!

---

### Post by daou on 2007-12-19
> **karesz said:**
> Thx.
I've tried btnx. btnx haven't installed from deb, compiled, working. btnx-config installed from deb. When i'm rolling the side wheel, it's saying, the button is already detected. But i'll keep trying!

Did you try changing your Option "Device" to "/dev/psaux", Option "Protocol" to "auto" and removing the ButtonMapping Option?

If those don't help, it's possible that the side wheel doesn't conform exactly to PS/2 specs and it falls back on a default setting, acting like the normal wheel. If the mouse manufacturer supplies Windows drivers for the mouse, it could very well be the case.

---

### Post by daou on 2007-12-19
By the way, the btnx-config .deb worked for Ubuntu 7.10?

---

### Post by karesz on 2007-12-19
It is connected to an usb port and not to ps/2, do i have to change Option "Device" to "/dev/psaux" ? Or change it to /dev/usbdevXX.XX epXX (I think this last would be a stupid idea:) ) ? 
Yes, btnx-config .deb worked very well.

---

### Post by karesz on 2007-12-19
Well. I've tried your advices, but it seems that it is not working. then i've set up with 8 buttons, but i've found that firefox opened each link in a different window, back-forth didn't do anything, only the wheel and the 6th btn did what i told them to do...

Btw: What could be the problem with evdev?

---

