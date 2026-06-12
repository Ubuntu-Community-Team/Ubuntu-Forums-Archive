---
title: "Elo Touch Screen Ubuntu 9.04"
date: 2009-07-07
forum: Hardware
---

### Post by _UsUrPeR_ on 2009-07-07
Having some major issues getting my Elo Touchscreen working in Ubuntu 9.04.

I am not able to use an xorg.conf like I used to which, it appears, is still required to properly calibrate the touch area.

To explain: I am using an Elo 1529L Entuitive touch screen. When I plug it's USB interface into a Ubuntu 9.04 PC, it's touch Y-calibration is reversed (I.E. If I touch the upper-right, it puts the cursor in the lower-right). On top of that, the touch screen is out of calibration. It appears to be operating in a screen that is 800x600, so ifI have my finger in the upper-right corner, the mouse will be where a 800x600 monitor would end in the lower-right.

Can anyone point me towards a good solution to get this working? I have thus far tried Serial and USB. Serial does not seem to want to work with X at all.

Strangely enough, if I do the following while the Serial plug is plugged in, I can get output from the monitor:

```
ubuntu@ubuntu:/# cat /dev/ttyS0
```

Trying to assign this to mouse movement has proven quite tricky.

Thanks.

---

### Post by life4himsq on 2009-08-02
I have an EloTouch monitor that shows up as a 2500u. After lots of looking and not wanting to compile drivers and such, I got it to work by getting parts from many forums. A few weeks after getting it to work I thought I would try it again from scratch to see if I could do it again. The first time was ubuntu 8.10 32bit and this time I am running ubuntu 9.04 64bit. I couldn't remember how I did it so after searching I was brought here. I have got it working now so I thought I would let you know what I have done now to get it working. I don't know that much about the hardcore linux yet, but I know this has worked twice so far rather painlessly.



First you need to find out where the usb is located in the system. Type this in the console.

cat /proc/bus/input/devices

Should return a lot of stuff and one section should have the name of your monitor. Here is what I got.

I: Bus=0003 Vendor=04e7 Product=0007 Version=0100
N: Name="Elo TouchSystems, Inc. Elo TouchSystems IntelliTouch 2500U"
P: Phys=usb-0000:00:02.0-4/input0
S: Sysfs=/devices/pci0000:00/0000:00:02.0/usb2/2-4/2-4:1.0/input/input6
U: Uniq=070kodak
H: Handlers=mouse2 event6 js0 
B: EV=1b
B: KEY=10000 0 0 0 0
B: ABS=10000000003
B: MSC=10


The event# on the Handlers= line will be used later. If you want to make sure you have the right number, you can type cat /dev/input/event6 replacing 6 with the number you found on yours. If you want to make sure you found the right event number, just type this into a console and touch the screen. Again, change the 6 to the number you found above.

> cat /dev/input/event6

You should see a lot of random stuff fly up the console.


Following all the other formums, I ended up using driver xserver-xorg-input-evtouch. I have not tested to see if xserver-xorg-input-elographics works with the way I am doing it. You can try either one. You can install the driver with synaptic or the console. For the console just type

sudo apt-get install xserver-xorg-input-evtouch



The xorg.conf might look like it is empty and not usable, but it is. I assume most of the info is missing because it is made up on the fly every time you boot so as to save clutter in the xorg.conf. You can edit xorg however you want to, I just typed "sudo gedit /etc/X11/xorg.conf" in a console. I put this near the top, right under the all the remarks and stuff.

> #Virtual Device "touchscreen" defined by udev rule in /etc/udec/rules.d
Section "InputDevice"
Identifier "touchscreen"
Driver "evtouch"
Option "device" "/dev/input/event6"
# Option "device" "/dev/input/touchscreen"
Option "MinX" "0"
Option "MinY" "0"
Option "MaxX" "4096"
Option "MaxY" "4096"
Option "MoveLimit" "1"
Option "sendCoreEvents" "On"
Option "SwapY" "On"
Option "SwapX" "On"
EndSection

Section "ServerLayout"
Identifier "Default Layout"
screen "Default Screen"
InputDevice "touchscreen" "SendCoreEvents"
EndSection

I had to play with the numbers for minx,y and maxx,y until the touch matched the screen. It really wasn't as hard as it sounds. FYI, I am running at 1024x768. Now just restart and it should work. Let me know if you have any questions.

---

### Post by _UsUrPeR_ on 2009-08-02
Hey cool. Thanks for the write-up! I'll have to give this a try when I get a chance.

---

### Post by Wolfhere on 2009-09-10
life4himsq - Dude! You are awesome. Your xorg worked for me except, I turned SwapY off. Works perfectly! Thank you.

---

