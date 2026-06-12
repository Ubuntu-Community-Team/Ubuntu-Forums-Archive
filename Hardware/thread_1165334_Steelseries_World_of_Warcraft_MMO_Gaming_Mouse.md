---
title: "Steelseries World of Warcraft MMO Gaming Mouse"
date: 2009-05-20
forum: Hardware
---

### Post by Daktar on 2009-05-20
Im wondering if its possible to get all buttons to work with this mouse? Atm I can only get left/right button, scroll buttons and two buttons on left side to work.

---

### Post by HH60Gunner on 2009-11-02
Would be awesome if someone knew how to get this to work.  Just replaced my razer lachesis which was nice because it stored it's hotkeys in in-mouse memory so I could program it in windows then use it in linux.  However the wow mouse does not do that.  It's just too bad the lachesis had shitty button placement.

---

### Post by beeboob on 2009-11-04
I will also love, to know or get some tips go get this working. 

I have try whit imwhell, evdev, btnx etc. to get so many of they "17" buttons to working. 

But can only get, Button 1, 2, 3, 4, 5, 10, 11 to show up in xev. Where 4 & 5 wheel.

The cat /proc/bus/input/devices

I: Bus=0003 Vendor=1038 Product=0777 Version=0110
N: Name="SteelSeries World of Warcraft MMO Gaming Mouse"
P: Phys=usb-0000:00:1d.0-2/input0
S: Sysfs=/devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0/input/input3
U: Uniq=
H: Handlers=mouse1 event3 
B: EV=17
B: KEY=1f0000 0 0 0 0 0 0 0 0
B: REL=103
B: MSC=10

egrep "Name|Handlers" /proc/bus/input/devices

N: Name="SteelSeries World of Warcraft MMO Gaming Mouse"
H: Handlers=mouse1 event3

xinput list

"SteelSeries World of Warcraft MMO Gaming Mouse"	id=7	[XExtensionPointer]
	Type is MOUSE
	Num_buttons is 13
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

---

### Post by HH60Gunner on 2010-01-25
anyone ever able to have any luck with this?  I would love to play my wow on linux again, but I just can't do so without all of my hotkeys working.  Guess I should have bought another razer mouse since my last one I could set the hotkeys in windows and it would keep it in memory on the mouse and work in linux.

---

### Post by HH60Gunner on 2010-02-05
for people smarter than myself steelseries's website states that they have no intention of going out of thier way to make this mouse in linux however they would be willing to help any developers to make this mouse work in linux.  I think getting gaming hardware to function properly in linux is one step in the right direction.  I know if my mouse hotkeys worked properly in linux I would drop my windows partition all together.  The only thing keeping me going back to windows is the fact that my hotkeys on my gaming keyboard and mouse both work in windows but don't in linux, and hot keys are a serious gamers best friend.

---

### Post by taurolyon on 2010-02-21
I just wanted to voice my interest in this particular mouse, as this is the current mouse I am using.

I'm going to delve deeper into configuring this mouse, but I was wondering if anyone happened to know any device-monitoring utilities? Specifically, I was wondering if Ubuntu actually was able to see any particular signal when one of the "dormant" mouse buttons are pressed.

I did research the Microsoft Intellimouse, which has some additional buttons (side/tilt scroll, etc.) and found some successful tutorials on how to program the Intellimouse for use under Ubuntu.


As stated above, and on the manufacturer's site: [http://faq.steelseries.com/questions/19/Where+can+I+get+World+of+Warcraft+MMO+drivers+for+the+Linux+platforms](http://faq.steelseries.com/questions/19/Where+can+I+get+World+of+Warcraft+MMO+drivers+for+the+Linux+platforms).
> Unfortunately we do not have any plans to develop  proprietary **Linux** **drivers** anytime soon for the WoW Mouse, but we would  happily assist any community-driven efforts to develop an open-source  solution for Linux.community-driven efforts to develop an open-source  solution for Linux.

---

### Post by taurolyon on 2010-02-21
```
xinput get-button-map "SteelSeries World of Warcraft MMO Gaming Mouse"
```> 1 2 3 4 5 6 7 8 9 10 11 12 13 It appears it recognizes 13 out of the total 17 buttons (human interface functions [15 buttons & scroll up/down])

Does anyone have a How-To on how to map these buttons?



```
xinput list-props "SteelSeries World of Warcraft MMO Gaming Mouse"
```> Device 'SteelSeries World of Warcraft MMO Gaming Mouse':
    Device Enabled (115):    1
    Evdev Reopen Attempts (247):    10
    Evdev Axis Inversion (248):    0, 0
    Evdev Axis Calibration (249):    
    Evdev Axes Swap (250):    0
    Evdev Middle Button Emulation (251):    2
    Evdev Middle Button Timeout (252):    50
    Evdev Wheel Emulation (253):    0
    Evdev Wheel Emulation Axes (254):    0, 0, 4, 5
    Evdev Wheel Emulation Inertia (255):    10
    Evdev Wheel Emulation Timeout (256):    200
    Evdev Wheel Emulation Button (257):    4
    Evdev Drag Lock Buttons (258):    0



```
xinput query-state "SteelSeries World of Warcraft MMO Gaming Mouse"
```
> 2 classes :
ButtonClass
        button[1]=up
        button[2]=up
        button[3]=up
        button[4]=up
        button[5]=up
        button[6]=up
        button[7]=up
        button[8]=up
        button[9]=up
        button[10]=up
        button[11]=up
        button[12]=up
        button[13]=up
ValuatorClass Mode=Relative Proximity=In
        valuator[0]=730
        valuator[1]=133

---

### Post by taurolyon on 2010-02-21
Through my own experimentation, I have determined the following:
```

button[1]=Left Click
        button[2]=Middle Click (scroll wheel press)
        button[3]=Right Click
        button[4]=Scroll Up
        button[5]=Scroll Down
        button[6]=??????
        button[7]=??????
        button[8]=Thumb button (lower)
        button[9]=Thumb button (upper)
        button[10]=??????
        button[11]=??????
        button[12]=??????
        button[13]=??????
```

I've attempted to use XEV to determine if the mouse appears to be outputting anything when the other 10 mouse buttons are pressed, and I have seen nothing. I'm not sure if the OS isn't recognizing it, or if an additional Human-Interface-Device driver would need to be installed to see these specific buttons (like a joystick).

So, to conclude, the buttons that are **_not_** working:
Left side, thumb 4-way directional pad
Right Side, up/down 2-way
Top, 2 either side of scroll wheel and 2 below scroll wheel

---

### Post by Raucabe on 2010-05-25
Would really like for someone to fix this or find some solution

---

