---
title: "Logitech G5 mouse on Feisty?"
date: 2007-04-21
forum: Hardware &amp; Laptops
---

### Post by PARTyZAN on 2007-04-21
Has anyone made the side (back) button of Logitech G5 mouse to work under Feisty? I followed few howtos for Logitech MX series, but none of them seem to work for me. Any suggestios?

---

### Post by danbh on 2007-05-03
[http://adterrasperaspera.com/blog/2006/06/20/logitech-g5-review-under-linux/](http://adterrasperaspera.com/blog/2006/06/20/logitech-g5-review-under-linux/)

---

### Post by PARTyZAN on 2007-05-03
I already followed this howto. My side button still didn't work.

---

### Post by silent_ on 2007-05-28
I'm looking into this as well... the button is button 6 if that helps any. left click is 1, right click 2, 3 probly press wheel, 4+5 scroll up/down 7+8 tilt left/right

---

### Post by magik on 2007-06-10
The author of the above mentioned article mad a minor mistake in his how to. The side button is actually Button 8. Also, as mentioned earlier, its up to the program to utilize the button. If your trying to test the side button in firefox and expect the browser to jump back a page, it simply will not work that way. Firefox is set up to use the tilt left and right buttons to jump forward and backward. Here is a snippet of what your xorg.conf file should look like.
> Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"evdev"
	Option		"Name" "Logitech USB Gaming Mouse"
	Option		"CorePointer"
#	Option		"Device"		"/dev/input/mice"
#	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5 6 7 8"
	Option		"Emulate3Buttons"	"true"

The options "Device" and "Protocol" are commented out, be sure you do that otherwise X will not be able to restart. Possible an unsupported feature in the evdev driver. To comment out the lines simply put a hash mark "#" in front of the line or delete it entirely if you like. The buttons are mapped as follows.

Button 1    Left Button
Button 2    Right Button
Button 3    Scroll Wheel Button
Button 4    Mouse Wheel Up / Down
Button 5    Mouse wheel Up / Down
Button 6    Mouse wheel tilt left / right
Button 7    Mouse wheel tilt left / right
Button 8    Lower Left Button (Thumb Button)

---

### Post by General_Ts0 on 2007-07-01
I tried this an now only tilt right works as "back" button in Firefox, tilt left does nothing nor does thumb.. All I'm really trying to accomplish is mainly using thumb button as back.  Though I could live with tilt left = back and tilt right = forward.

---

### Post by linuxwizard on 2007-07-01
[https://help.ubuntu.com/community/ManyButtonsMouseHowto#head-c0a8007b2ea8ddcdd7507827a1007e4c2fa6c7b4](https://help.ubuntu.com/community/ManyButtonsMouseHowto#head-c0a8007b2ea8ddcdd7507827a1007e4c2fa6c7b4)

---

### Post by eschatologicalhumor on 2007-07-15
[http://doc.gwos.org/index.php/LogitechMouse](http://doc.gwos.org/index.php/LogitechMouse)

This worked to get my back button on the left side of my mouse to work.
One issue with this tutorial is that the logitech_applet 'wget' command does not work. apparently it is no longer on that site. I get a "FORBIDDEN" error, so download the source and install it yourself, then continue on with the tutorial.

My issue is now getting my left/right toggles to work. Does adding 2 unused numbers into the 'ZAxisMapping' section work?

---

### Post by eschatologicalhumor on 2007-07-15
magik, your snippet of xorg.conf worked beautifully!

now not only does my back button still work(always did), but my side toggles work as well!

AWESOME man.

Now, the question is, can i program them in ET and other games/programs?

---

### Post by daou on 2007-07-15
btnx-0.2.14 supports G5.
I recommend the newer version (btnx-0.3.1 with btnx-config-0.1.7) which has a GUI for configuring the buttons + other useful features.

Check this thread for more info: [http://ubuntuforums.org/showthread.php?t=455656](http://ubuntuforums.org/showthread.php?t=455656)

---

### Post by Naegling23 on 2007-10-02
Hmm, so I have the g5 with two side buttons.  All of the buttons work fine except the scroll side to side.  Here is my xorg.conf:

Section "InputDevice"
  # generated from default
  Identifier "Mouse0"
  Driver "mouse"
  option "Protocol" "auto"
  option "Device" "/dev/psaux"
  option "Emulate3Buttons" "no"
  option "ZAxisMapping" "4 5 8 9"
  option "Buttons" "9"
  option "ButtonMapping" "1 2 3 6 7"
EndSection

I tried adding the changes listed in this thread, but it causes x to crash/not load, with an error about Mouse0 or core pointer.  Any suggestions?

---

### Post by Naegling23 on 2007-10-02
nevermind, I figured it out, im sure someone else will have the same issue

You also need to change the input device under server layout to whatever your mouse name is....silly me.

so if your identifier is logitech mouse, your input device should also be logitechmouse

hope this helps someone in the future

---

### Post by benhagerty on 2007-10-02
ah thanks, was just trying to figure it out

---

### Post by D-EJ915 on 2007-10-03
also if you want to know what button is being "used" open up a terminal type in "xev" and stick the mouse over the box (keep it still otherwise it will tell you everytime it moves) and click all the buttons.

---

### Post by adrift on 2007-10-20
> **daou said:**
> btnx-0.2.14 supports G5.
I recommend the newer version (btnx-0.3.1 with btnx-config-0.1.7) which has a GUI for configuring the buttons + other useful features.

Check this thread for more info: [http://ubuntuforums.org/showthread.php?t=455656](http://ubuntuforums.org/showthread.php?t=455656)

Awesome. For those scratching thier head after installing this the command for the left thumb button on a Logitech G5 mouse to go back a page is Keycode: Key_Left and Modifier Key 1: Key_Leftalt

---

### Post by jdorwin on 2008-03-12
Just use this:

Section "InputDevice"
Identifier "Configured Mouse"
Driver "evdev"
Option "CorePointer"
Option "Name" "Logitech USB Gaming Mouse"
Option "ZAxisMapping" "4 5 6 7"
Option "Emulate3Buttons" "false"
EndSection

All the features of the mouse, including the tilt wheel, will function.

---

