---
title: "eGalaxTouch touchscreen clicks on second tap"
date: 2010-05-07
forum: Hardware
---

### Post by naugtur on 2010-05-07
I have installed eGalaxTouch drivers for my usb touchscreen and they work fine (on ubuntu 8.04, I had problems with newer versions).
The problem is that when I tap the screen the cursor moves there and if I tap there again only then the click happens. 

It's probably supposed to be a correct behaviour, but it's not acceptable in my case. How can I configure it to click on every tap?

---

### Post by sprince09 on 2010-05-07
There should have been some sort of utility that got installed along with the driver that let's you modify the behavior of the touchscreen. I think it's called eGalaxtouch or something like that. Try running sudo eGalaxtouch (try using tab completion to find the right command) from the command line.

---

### Post by naugtur on 2010-05-07
I used the utility to calibrate positions. I also looked through all the avaliable options. Most of them are disabled and I have no idea why. 

I saw no options that could affect clicking. 
"current mode" might change something, but change option is also disabled. The value is set to "normal"
I suppose there is a file where the settings are kept. Or maybe I can set it up in xorg.conf somehow.

---

### Post by sprince09 on 2010-05-07
I had that same problem (greyed out settings boxes) on my eGalax too... I never figured out a way to fix it. I couldn't get the eGalax driver to work at all in Lucid so I'm not sure what else to do.

---

### Post by naugtur on 2010-05-10
Solved with ubuntu 10.04
[not sure, but it might work with earlier versions.]

Without installing the eGalaxTouch support I got everything working great with default evdev setup in ubuntu 10.04 adding these commands to fix the old problems with rotation / swapped axes. Correct tap behaviour was present out-of-the-box.

```
xinput set-prop --type=int --format=8 "eGalax Inc. USB TouchController" "Evdev Axes Swap" 1
```fixed the swap

if Y is inverted, use this:
```
xinput set-int-prop "eGalax Inc. USB TouchController" "Evdev Axis Inversion" 8 0 1
```

and then calibration:
```
xinput set-prop --type=int --format=32 "eGalax Inc. USB TouchController" "Evdev Axis Calibration" 57 1938 162 1979
```to get Your own calibration numbers You need this:
[http://www.freedesktop.org/wiki/Software/xinput_calibrator](http://www.freedesktop.org/wiki/Software/xinput_calibrator)

building from source:

#for fresh desktop install You'll need some packages:
```
sudo apt-get install g++ autoconf libtool xorg-dev
```unpack the calibrator, cd to the folder and run 
```

./autogen.sh
make

```cd to the src folder and run
```
 ./xinput_calibrator_x11 
```do the clicks and it will write Your config to console.

binary built on ubuntu 10.04 32bit 
[ATTACH]156303[/ATTACH]

---

### Post by sprince09 on 2010-05-10
Awesome, I'll try this when I get home :)

---

### Post by sprince09 on 2010-05-16
Well, no success for me... touching the screen still just makes the cursor fly around randomly :(

---

### Post by naugtur on 2010-05-17
Are You sure You're trying this on Ubuntu 10.04? When I was using 8.04 it didn't work.

Also call
 ```
xinput list
```and see if Your device name is the same as in my example. You might have it under a different name there.

"eGalax Inc. USB TouchController" is what showed up on the list on my machine.


And if it really moves "randomly" (in a manner that seems unrelated to Your finger movement) then I think data from the device is being interpreted as from ordinary mouse. I have no idea how, but You might need to disable the classic mouse driver.

---

### Post by reckik on 2010-05-21
Hi naugter,

Im having the same issues. Tried to xinput set-prop and it was unable to find the device.

Heres my xinput list

> &#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; EVTouch TouchScreen                     	id=10	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=14	[slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation        	id=15	[slave  pointer  (2)]
&#9116;   &#8627; EVTouch TouchScreen                     	id=11	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=9	[slave  keyboard (3)]
    &#8627; Acer Crystal Eye webcam                 	id=12	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=13	[slave  keyboard (3)]


I see EVTouch two times there. Tried instead of "Egalax Inc. USB TouchController" the "EVTouch Touchscreen" but still unable to find the device.

Next i went to /dev/input/by-id/usb-eGalax_Inc._USB_TouchController-event-if00 just for experiment, but didnt work either. 

With ur attatchment the calibration did seem to work, at least it registred the touch on the screen.

Hope u can help, the touchscreen worked fine in 9.10. In the end i ended up editing the evtouch calibration file manually. Can that still be done?

PS - reacted to u in another threat to, but didnt see it was marked as solved already

thx for ur help

---

### Post by naugtur on 2010-05-22
It should be eGalax... not EVTouch TouchScreen, but the problem isn't there.

You have it twice on the list, so You probably calibrate only one of them and it's not the right one. Try putting id numbers instead of "eGalax...". 
And do a search for problems with touchscreen driver appearing twice. I saw a few of those.

---

### Post by reckik on 2010-05-23
hmm not sure what happened here during the weekend. I think some 'kaboutertjes' have sneaked in and fixed my touchscreen.

Appearently after rebooting my xinput list did gave a Egaalax inc. usb touchcontroller. 

Also the touchscreen calibration appeared again. egalax_calibrator_x11.
Calibrated it and did the trick.

Now just fixing the right click.....

---

### Post by naugtur on 2010-05-23
I can't help You with the right click, because no right click was a feature for me ;) I needed to block it. Ubuntu did it for me ;)

Take look in the moise settings applet from System menu. It has some new accessibility features on ubuntu 10 as far as I remember.

But I saw some old rightclick threads. You could post a link here to a thread that helps You. For future reference

---

### Post by reckik on 2010-05-26
well that was actually 2 easy that i looked way 2 hard. Didnt read ur last post to good either, could have saved me a lot of time. 

Did what u said, went to system - mouse - accessibility feature and enabled, Selected how long the click should last for the secondary menu to appear and that works so thats great. The only thing is that the 'secondary click' only appears after releasing the screen, so u practically have to count, it doesnt appear like that.

---

