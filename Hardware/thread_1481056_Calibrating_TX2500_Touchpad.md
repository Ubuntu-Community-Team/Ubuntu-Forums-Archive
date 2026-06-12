---
title: "Calibrating TX2500 Touchpad"
date: 2010-05-12
forum: Hardware
---

### Post by Drycola on 2010-05-12
Hello,

I'm not sure if this was asked before but all I found in search just confused me even more!!
I have an HP TX2500 Tablet PC with a touchscreen (wacom, I guess). It is working greatly except that it is not well calibrated, I can't reach the main menu while in fact I'm physically pressing on it.
I need to calibrate the touchscreen, **How can I calibrate the touchscreen??**

---

### Post by Favux on 2010-05-12
Hi Drycola,

This thread  has the calibrations, see post# 4:  [http://ubuntuforums.org/showthread.php?t=1478728](http://ubuntuforums.org/showthread.php?t=1478728)  You may need to fine tune it a little.  You should also be able to calibrate it with xsetwacom commands.

---

### Post by Drycola on 2010-05-12
I have suffered for several hours to get my touchscreen calibrated!!!
So, after reading several articles (many are useless) and a number of try-and-fail processes I've found the best simple way for that!!!
I'm posting it here hoping that other HP TX2510us Users won't suffer the same issues again!

So here is it:
[B]
How to calibrate HP Tx2510us (tx2500 series) Touchscreen and Stylus:
Run terminal
within terminal enter the following commands:

[/B]> xsetwacom set "12" TopX 225 
xsetwacom set "12" TopY 225 
xsetwacom set "12" BottomX 26300 
xsetwacom set "12" BottomY 16375
 
xsetwacom set "13" TopX 200 
xsetwacom set "13" TopY 225 
xsetwacom set "13" BottomX 4000 
xsetwacom set "13" BottomY 3872

Please note that this is strictly for HP TX2500 (the 12 & 13 above specify the device ID for the hardware used in this tablet), so please DON'T USE THIS FOR OTHER TABLETS, PLEASE...

---

### Post by Favux on 2010-05-12
Hi Drycola,

That looks good.  I'm not sure you need the quotes around the Device ID numbers.

Since Lucid doesn't have wacomcpl you have to do it manually.  Wacomcpl would lead you through the calibration routine and then add the calibration xsetwacom commands to it's script file .xinitrc.  You'll have to make one yourself so the calibration is applied everytime you start.  Create a file, say .xsetwacom.sh and place the xsetwacom commmands in it.  Make it executable and set it to run with auto-start and you should be good.

---

### Post by Drycola on 2010-05-13
Thanks for that important tip, I've already figured that calibration is temporary so I had put my commands in an .sh file and I've done it before reading your post!
But it is good that you wrote it here so that others can use it too..
Thanks

---

### Post by Rehellio on 2012-06-22
For those who found this thread and are wonder how to convert it to the new parameter Area, I found this setting works.

```
xsetwacom set "Wacom ISDv4 93 Finger touch" Area 181 177 3914 3899
```

Make sure to change "Wacom ISDv4 93 Finger touch" to what your computer says it is. If your wondering how to do that here the command.

```
xsetwacom --list devices
```

And look for the one that is associated with the touchscreen

```
user@Computer:~$ xsetwacom --list devices
Wacom ISDv4 93 Pen stylus       	id: 11	type: STYLUS    
Wacom ISDv4 93 Finger touch     	id: 12	type: TOUCH     
Wacom ISDv4 93 Pen eraser       	id: 18	type: ERASER 
```

How I found it out was through the xinput_calibrator tool

```
 sudo apt-get install xinput-calibrator 
```

and used this command to calibrate it

```
 xinput_calibrator --device "Wacom ISDv4 93 Finger touch" 
```

replace "Wacom ISDv4 93 Finger touch" from the list devices option in xsetwacom

do the program and it will spit out code on the terminal similar to this

```
user@computer:~$ xinput_calibrator --device "Wacom ISDv4 93 Finger touch"
Calibrating standard Xorg driver "Wacom ISDv4 93 Finger touch"
	current calibration values: min_x=0, max_x=4095 and min_y=0, max_y=4095
	If these values are estimated wrong, either supply it manually with the --precalib option, or run the 'get_precalib.sh' script to automatically get it (through HAL).


--> Making the calibration permanent <--
  copy the snippet below into '/etc/X11/xorg.conf.d/99-calibration.conf'
Section "InputClass"
	Identifier	"calibration"
	MatchProduct	"!!Name_Of_TouchScreen!!"
	Option	"MinX"	"155"
	Option	"MaxX"	"3936"
	Option	"MinY"	"150"
	Option	"MaxY"	"3880"
EndSection
```

Then open your text editor to where you place your paramaters for you wacom devices or just make a new one and type the xsetwacom paramater in there

example:
```
xsetwacom set "Wacom ISDv4 93 Finger touch" Area 181 177 3914 3899
``` 

Area x1 y1 x2 y2
MinX = x1
MaxX = x2
MinY = y1
MaxY = y2

Note: this was done on a HP TX 2500 so it may be different on other machines.

---

