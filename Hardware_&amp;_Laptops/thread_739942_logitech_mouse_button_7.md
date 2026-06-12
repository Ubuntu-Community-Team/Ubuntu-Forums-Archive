---
title: "logitech mouse button 7"
date: 2008-03-30
forum: Hardware &amp; Laptops
---

### Post by starling on 2008-03-30
I have a logitech LX5 mouse with the normal 3 buttons + horizontal scroll, making 7 buttons. Under the default drivers 3 buttons + scroll work, but rocker-left acts as another middle button, and rocker-right does nothing.
After reading a few threads, I changed the driver to explorerPS/2 and now the rocker-left works but rocker-right is still not responding. I ran xev and right-rocker is not being mapped.

The entry in xorg.conf looks like this:
```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ExplorerPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
	Option		"Buttons"	"7"
	Option		"ButtonMapping"	"1 2 3 6 7"
EndSection
```

And cat /proc/bus/input/devices has this entry:
```
I: Bus=0003 Vendor=046d Product=c50c Version=0110
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:03.1-1/input1
S: Sysfs=/class/input/input3
U: Uniq=
H: Handlers=kbd mouse1 event3 
B: EV=f
B: KEY=7fff 42c332f bf084440 0 0 ff0001 1f84 8837cc00 667bfa dd71dfed 9e0000 0 0 0
B: REL=1c3
B: ABS=1 0
```

For reference the mouse shares it's receiver dongle with a keyboard.
There's plenty of similar threads, but most seem to be Dapper vintage. I have Gusty.

Can anyone help with this?
Thanks.

---

### Post by starling on 2008-03-31
Is this worth a bump?

---

### Post by Vienna01 on 2008-04-08
I have the Logitech Cordless Optical LX5 mouse too. 

XEV says it handles the buttons as follows:
Left click Button 1
Right click Button 3
Roll center wheel forward Button 4
Roll Center wheel backward Button 5
Press center wheel Button 2

The part number for my mouse is 831906-0000, the PID is LZ701A6
Some photos of the LX5 on the net refer to a different PN 931451-0914.

The RECEIVER PN is 831511-0000 PID LZ652AS      
MN:C;BT44( I don't know what this means)
The mouse doesn't say LX5 anywhere but I compared it to references/images on the net.
I purchased the mouse as part of a kit with the S510 keyboard. The receiver that the mouse & KB talk to has a PS/2 connection for the mouse terminal and a USB with an PS/2 adapter for the KB connection.

Hope this helps some.

---

