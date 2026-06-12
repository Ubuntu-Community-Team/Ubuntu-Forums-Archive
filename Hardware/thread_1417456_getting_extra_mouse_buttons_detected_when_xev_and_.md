---
title: "getting extra mouse buttons detected when xev and evdev don't see them"
date: 2010-02-27
forum: Hardware
---

### Post by urlwolf on 2010-02-27
I got this mouse:
saitek comfort laser mouse
[http://www.saitek.com/UK/PROD/pm37.htm](http://www.saitek.com/UK/PROD/pm37.htm)

it has 9 buttons (if you count scroll wheel up & down) but two of the buttons are not detected when xev and evdev run:

```

root@/usr/share/texmf-texlive/tex/latex# cat /proc/bus/input/devices
...
I: Bus=0003 Vendor=06a3 Product=04e5 Version=0110
N: Name="Saitek Saitek Laser Office Mouse"
P: Phys=usb-0000:00:1d.1-1/input0
S: Sysfs=/devices/pci0000:00/0000:00:1d.1/usb6/6-1/6-1:1.0/input/input28
U: Uniq=
H: Handlers=mouse4 event11 
B: EV=17
B: KEY=1f0000 0 0 0 0
B: REL=103
B: MSC=10


root@/usr/share/texmf-texlive/tex/latex# evdev-key-btn-test /dev/input/event11
Supported Keys:
  Key  0x110  (Left Button)
  Key  0x111  (Right Button)
  Key  0x112  (Middle Button)
  Key  0x113  (Side Button)
  Key  0x114  (Extra Button)
Buttons/Keys:   5

Supported Relative axes:
  Relative axis 0x00  (X Axis)
  Relative axis 0x01  (Y Axis)
  Relative axis 0x08  (Vertical Wheel)

```
So as you see, only 5 buttons.

xev doesn't see them when I press them. Neither does imwheel or xbtn.

I'm on ubuntu karmic, by default buttons 1-32 are registered. I've seen logitech mice use buttons 11 - 13 on the same computer.

Any idea what to try next? No manual available from saitek...

---

### Post by urlwolf on 2010-02-27
just wanted to add:
```

$xinput list
"Saitek Saitek Laser Office Mouse"	id=11	[XExtensionPointer]
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


``` 

linux sees the buttons, but it doesn't know when I pressed them:
Pressing an ok button (back)
```
 

xinput query-state "Saitek Saitek Laser Office Mouse"
2 classes :
ButtonClass
	button[1]=up
	button[2]=up
	button[3]=up
	button[4]=up
	button[5]=up
	button[6]=up
	button[7]=up
	button[8]=up
	button[9]=down
	button[10]=up
	button[11]=up
	button[12]=up
	button[13]=up
ValuatorClass Mode=Relative Proximity=In
	valuator[0]=454
	valuator[1]=599

``` 

this is pressing some of the missing buttons
```
 

quesada@~> xinput query-state "Saitek Saitek Laser Office Mouse"
2 classes :
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
	valuator[0]=454
	valuator[1]=599

```

---

### Post by AuraDevil on 2010-02-28
Hello, Have you had any luck with this? I'm having a similar problem with my Saitek Cyborg mouse

---

