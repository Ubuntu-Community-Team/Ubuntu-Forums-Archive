---
title: "Touchscreen calibration problem"
date: 2009-05-03
forum: Hardware
---

### Post by 7th on 2009-05-03
OK, I have a Acer Aspire One with a touchscreen mod

I've just installed the netbook remix (9.04 jaunty) and the touchscreen is detected and works using the live usb and on the subsequent install in everything (click, drag, full screen range etc) except one important point - 

All the axis are reversed :confused:

The calibration tool put the y-axis the right way up (though the x-axis are still reversed) but it will no longer move the pointer to the end of the screen and the x-axis movement appears to be magnified

I've spent the last couple of day googling for solutions using the xorg.conf and installing/installing drivers to the point where I've just re-installed to try again :-|

From what I found I suspect there is a xorg option to flip the axis but I can't figure out how (I won't be trying the calibration tool again - it all went downhill from there) :-|

Any help appreciated, with thanks

PS the touchscreen worked fine in 8.10 using egalax/TouchKit (this don't seem to work at all under 9.04)

---

### Post by warren94 on 2009-05-10
I am going to buy a touch screen soon, 
1. Where did you buy yours?
2. I will tell you when i have done mine.
Thanks and hope you fix your problem and will help me if possible.

---

### Post by arashiko28 on 2009-05-10
Have you tried to find a version for 9.04?

Also, on system>preferences>display you have an option, rotation, try it.

---

### Post by 7th on 2009-05-14
OK, I think I've almost fixed it (though the calibration program is still off)
The touchscreen is now the right way round and up, though accuracy isn't great (but that could be because it only a 4 wire touchscreen, but it _seemed_ more accurate under 8.10 with Touchkit). After a bit more Googling and playing around I came up with this work around:rolleyes: (at least until the calibration tool is fixed)

Use the 9.04 liveusb to boot into, run the calibration program and note down the numbers mentioned as min/max eg (96/186) and (3986/3956) during the calibration in the top left corner of the screen. The first number is the number is the X axis and the second is the Y.

I added these to the xorg.conf following the structure found on the evtouch website (you can also add this to the xorg.conf used in the live environment if you want to check out your setting before changing you actual system)

Open a terminal (Application/Accessories/Terminal)

sudo gedit /etc/X11/xorg.conf

(I always found that because I can't remember how to spell the commands half the time in bash, hit TAB to see your options/complete a command/directory is an invaluable key to remember)

Add these lines to xorg.conf:

Section "InputDevice"
	Identifier "touchscreen"
	Driver "evtouch"
	Option "Device" "/dev/input/event6"
	Option "MinX" "96"
	Option "MinY" "186"
	Option "MaxX" "3986"
	Option "MaxY" "3956"
	Option "SwapX"  "1"
	Option "SwapY"	"1"
	Option "SendCoreEvents" "On"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"touchscreen" "SendCoreEvents"
EndSection

It's important to put "Default Layout" and "Default Screen" into the ServerLayout if you've just created one otherwise it doesn't seem to work (thanks to whoever wrote it first, I remember reading while browsing for a solution but not where:-\").

The Option "Device" "/dev/input/event6" for which ever touchscreen you use can be found using the following commands (again from various website/thread I can't recall the address to, but all credit to the original authors)

cat /proc/bus/input/devices

In my case (amoung a whole lot of others) the output gave me

I: Bus=0003 Vendor=0eef Product=0001 Version=0210
N: Name="eGalax Inc. USB TouchController"
P: Phys=usb-0000:00:1d.7-5.1/input0
S: Sysfs=/devices/pci0000:00/0000:00:1d.7/usb1/1-5/1-5.1/1-5.1:1.0/input/input6
U: Uniq=
[COLOR="Blue"]H: Handlers=mouse1 event6 [/COLOR]
B: EV=1b
B: KEY=401 0 30000 0 0 0 0 0 0 0 0
B: ABS=f
B: MSC=10

Where H: Handlers (highlighted in blue) show your event number

Once you've got a working xorg.conf in the liveusb environment (ie one that doesn't crash X on logging out and login in again) remember to save it somewhere (the first time I didn't:redface:). You may also what to run

sudo dontzap --disable

to give you back the option to Crtl+Alt+Backspace to restart X (quick logout) as I found myself doing this a lot.

I used a usb 'no soldiering required' touchscreen kit from fidohub.com seeing as I'm not very experienced at soldiering (more expensive that way though).

What slightly annoys me is that the evtouch driver appears to work with most functions out of the box - click, double click, drag n drop, drag select etc but the calibration seems hopeless and any other functions are hidden from view (right click option anyone:?:).

---

### Post by Orwhaleca on 2009-09-16
the right click is holding it down for approx. 1-1.5 seconds. also, how did you switch the axis back to the way they should be? I can't seem to figure it out.

---

