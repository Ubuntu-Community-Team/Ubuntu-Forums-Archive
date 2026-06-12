---
title: "Huion H610 Drawing Tablet"
date: 2013-01-15
forum: Hardware
---

### Post by mladenkovacevic on 2013-01-15
So I purchased this Chinese made drawing tablet: [http://www.huion-tablet.com/product/product.php?sku=1004](http://www.huion-tablet.com/product/product.php?sku=1004)

It works excellent in Windows with the drivers they've provided and I managed to get it working in Linux almost perfectly by installing the wizardpen driver and using the following settings in the 52-tablet.conf file.

```

Section "InputClass"
    Identifier "UC-Logic tablet"
    MatchIsTablet "on"
    MatchProduct "HUION H610"
    MatchDevicePath "/dev/input/event*"
    Driver "wizardpen"
    # Apply custom Options below.
    Option    "TopX"    "0"
    Option    "TopY"    "0"
    Option    "BottomZ"    "2047"
    Option    "BottomX"    "2047"
    Option    "BottomY"    "2047"
EndSection

```

Even after applying these settings I find that the native Windows drives seems to be a little smoother and the button mapping is all wrong on Linux side as well. How can I modify these settings so that I get the best performance. I set BottomZ to 2047 because the tablet is advertised as having 2048 levels of pressure sensitivity. Am I doing this right? Another concern I have is that when pressure sensitivity is on line thickness, in Linux they look a little bit jagged, while in Windows they are perfect. Hope someone has some ideas. Thanks.

---

### Post by Favux on 2013-01-20
Hi mladenkovacevic,

Welcome to Ubuntu forums!


A little more information would be useful.  What release of Ubuntu are you using?  How did you install the WizardPen driver?  Why did you think that was the driver for your Huion?  What is the output of the following commands entered in a terminal (with the tablet plugged in)?
```
lsusb
*and*
xinput list
```

BottomZ at 2047 is correct and you could establish a pressure "threshold" if the tablet was too sensitive by say setting the minimum pressure to 5:
```
Option "TopZ" "4"
```
I am a little puzzled as to how the BottomX and Y are also 2047.  That seems a bit of a coincidence.  Makes me wonder if the tablet is actually on the WizardPen driver.

---

### Post by mladenkovacevic on 2013-01-21
> **Favux said:**
> Hi mladenkovacevic,

Welcome to Ubuntu forums!


A little more information would be useful.  What release of Ubuntu are you using?  How did you install the WizardPen driver?  Why did you think that was the driver for your Huion?  What is the output of the following commands entered in a terminal (with the tablet plugged in)?
```
lsusb
*and*
xinput list
```

BottomZ at 2047 is correct and you could establish a pressure "threshold" if the tablet was too sensitive by say setting the minimum pressure to 5:
```
Option "TopZ" "4"
```
I am a little puzzled as to how the BottomX and Y are also 2047.  That seems a bit of a coincidence.  Makes me wonder if the tablet is actually on the WizardPen driver.

Hi Favix. Thanks for your response.
I am on Ubuntu 12.04 LTS and I installed wizardpen by compiling from source (version 0.8.1 I believe). The reason I used the wizardpen driver is because I know fairly reliably that this Huion tablet uses the same UC-Logic digitizer that most of the tablets officially supported by the wizardpen use as well.

Here is the output of the lsusb command 
```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0424:2512 Standard Microsystems Corp. USB 2.0 Hub
Bus 002 Device 002: ID 045e:0023 Microsoft Corp. Trackball Optical
Bus 002 Device 003: ID 256c:006e  
Bus 001 Device 005: ID 0424:2602 Standard Microsystems Corp. USB 2.0 Hub
Bus 001 Device 006: ID 0424:2228 Standard Microsystems Corp. 9-in-2 Card Reader

```

I think that the line that refers to the tablet is one without any identifying information after the ID field (256c:006e)

Here is the output of the xinput list command
```
 Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; HUION H610                              	id=8	[slave  pointer  (2)]
&#9116;   &#8627; HUION H610                              	id=9	[slave  pointer  (2)]
&#9116;   &#8627; HUION H610                              	id=10	[slave  pointer  (2)]
&#9116;   &#8627; Microsoft Microsoft Trackball Optical® 	id=11	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Power Button                            	id=7	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=12	[slave  keyboard (3)]

```

I can also run xinput list-props 8... or xinput list-props 9 - the output is the same:
```
Device 'HUION H610':
	Device Enabled (139):	1
	Coordinate Transformation Matrix (141):	1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
	Device Accel Profile (259):	0
	Device Accel Constant Deceleration (260):	1.000000
	Device Accel Adaptive Deceleration (261):	1.000000
	Device Accel Velocity Scaling (262):	10.000000

```

I got to the 2047 values for both BottomX and BottomY is because when I first installed the wizrdpen driver I could only move the mouse pointer a little bit with the pen (only vertically and along the top third of the left-most edge). I figured I'd need to change some properties in /etc/X11/xorg.conf.d/52-tablet.conf as mentioned in one of the online guides I found. I ran the "xinput test 8" command (8 for the device ID) and got a readout of values as I moved the pen across the tablet. There were 3 values a[0], which responded to me moving the pen horizontally, the a[1], which responded as I moved the pen vertically, and the a[2] which seems to remain at 0 regardless of what I did. The a a[0] and the a[1] would only get as far as 2047 as I moved the mouse to the corners so I assumed that these were the "Bottom" values.

I am also confused by the different instructions for using custom settings I've seen online. Somewhere it says that I should change the /usr/lib/X11/xorg.conf.d/70-wizardpen.conf, another place mentioned that the /etc/X11/xorg.conf.d/52-tablet.conf file keeps these settings (this is the one I've used and it seems to work). Oh and when I run the xinput_calibrator it tells me to put the suggested values into /etc/X11/xorg.conf.d/99-calibration.conf

---

### Post by mladenkovacevic on 2013-01-21
Actually I just turned on "smoothing" as an option in GIMP and my lines are smooth as silk again :) I guess I just needed to familiarize myself with the software a little bit.

So I guess now all that I have to do is re-map the buttons on the tablet to perform their intended functions.

I would love to contribute my final settings to the future versions of the Wizardpen driver.. What's the best way to do that?

Also I would recommend this tablet to anyone out there looking for a really cheap one. The build quality seems excellent and the pen that comes with it feels very sturdy as well. Can't go wrong for $60 :p

---

### Post by Favux on 2013-01-21
Well, everything looks OK.  It seems to be on WizardPen because if it was on evdev it would say so in the list-props output.  We could check things out some more by looking at Xorg.0.log in /var/log.

/usr/share/X11/xorg.conf.d is where the Distos put their .conf files.  You are not suppose to use that location.  User custom .conf files belong in /etc/X11/xorg.conf.d.  So xinput_calibrator is telling you the correct location.  Although I doubt it really has to be 99.  By the way what coordinates is it recommending?

What runs last controls and /etc/X11/xorg.conf.d runs after /usr/share/X11/xorg.conf.d.  And that's the same reason the .conf files have a number.  That way you can choose when they run.

What specifically is the button mapping issue?

And the jagged line might indicate a filtering problem.  What applications are you seeing that in?  If it really is a UC-LOGIC digitizer or the equivalent I don't think trying to place the tablet on the wacom driver to get its filtering routines will work.  Edit:  Just caught your post it is Gimp and you fixed it.  Nice work!

---

### Post by mladenkovacevic on 2013-01-22
It's interesting that you mention the evdev driver because now that I look more carefully, half of my instructions on getting the tablet running came from evdev and half from wizardpen. I basically installed the wizardpen drivers correctly, but then proceeded to store my tablet settings in the 52-tablet.conf file which comes from the evdev instructions. I will try to rename me 52-tablet.conf file, then create the 70-wizardpen.conf file which is required by the wizardpen driver and I'll see what happens. The xinput-calibrator was basically recommending 2047 for BottomX and BottomY with top values being between 1 and 6.. it tells me a different value each time but I assume it's because I'm not 100% accurate when hitting the crosshairs in the calibrator.

The button mapping issue I'm referring to is with regards to the buttons located on the side of the tablet... they are supposed to do one thing as labeled (and as they function in windows), but they function slightly differently in Linux. I found a tutorial on how to re-map the keys so I don't imagine this will present a big problem :)

---

### Post by Favux on 2013-01-23
Actually that gets a bit complicated.  If they are buttons that emit key press and releases then they're handled by the evdev keyboard snippet and the button function is set in the kernel.  But I don't see how the Huion can be using the UC-LOGIC kernel driver unless their vendor and product IDs were in the UC-LOGIC kernel drivers.  So hmmm.

If they're the hotkey type then they shouldn't work because no ones written a driver for them I am aware of.

---

### Post by garby on 2013-05-11
> **mladenkovacevic said:**
> It's interesting that you mention the evdev driver because now that I look more carefully, half of my instructions on getting the tablet running came from evdev and half from wizardpen. I basically installed the wizardpen drivers correctly, but then proceeded to store my tablet settings in the 52-tablet.conf file which comes from the evdev instructions. I will try to rename me 52-tablet.conf file, then create the 70-wizardpen.conf file which is required by the wizardpen driver and I'll see what happens. The xinput-calibrator was basically recommending 2047 for BottomX and BottomY with top values being between 1 and 6.. it tells me a different value each time but I assume it's because I'm not 100% accurate when hitting the crosshairs in the calibrator.  The button mapping issue I'm referring to is with regards to the buttons located on the side of the tablet... they are supposed to do one thing as labeled (and as they function in windows), but they function slightly differently in Linux. I found a tutorial on how to re-map the keys so I don't imagine this will present a big problem :) 

 §1. **PARTIALLY SOLVED:** I used wizardpen driver from ppa (ppa:doctormo/xorg-wizardpen) and then configured the 70-tablet.conf and it works fine. But the cursor of the synaptic touchpad froze in the center. Right and left click works, only the mouse cursor does not move. However the cursor moves using the tablet pen, but the mouse cursor only freezes. Any inputs?  

Partially SOLVED: 
#touch /etc/modprobe.d/modules.conf
#echo "options psmouse proto=imps" > /etc/modprobe.d/modules.conf
#reboot
 
It works. **BUT, not traditional unix copy by seclecting the text and pasting by selecting both right+left buttons in touchpad or middle mouse button stopped working.** Hmmm. This happened only after installing the wizardpen driver and making necessary configurations changes to 70-wizardpen.conf.

my xinput list looks as follows:

> $ xinput list
&#65533; Virtual core pointer                        id=2    [master pointer  (3)]
&#65533;   &#65533;&#65533;&#65533; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#65533;   &#65533;&#65533;&#65533; HUION H610                                  id=9    [slave  pointer  (2)]
&#65533;   &#65533;&#65533;&#65533; HUION H610                                  id=10    [slave  pointer  (2)]
&#65533;   &#65533;&#65533;&#65533; HUION H610                                  id=11    [slave  pointer  (2)]
&#65533;   &#65533;&#65533;&#65533; SynPS/2 Synaptics TouchPad                  id=13    [slave  pointer  (2)]
&#65533; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#65533;&#65533;&#65533; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#65533;&#65533;&#65533; Power Button                                id=6    [slave  keyboard (3)]
    &#65533;&#65533;&#65533; Video Bus                                   id=7    [slave  keyboard (3)]
    &#65533;&#65533;&#65533; Power Button                                id=8    [slave  keyboard (3)]
    &#65533;&#65533;&#65533; AT Translated Set 2 keyboard                id=12    [slave  keyboard (3)]
    &#65533;&#65533;&#65533; Toshiba input device                        id=14    [slave  keyboard (3)]

**UNSOLVED:** §2. It will also be nice to know the reconfiguration of the 8 hard buttons on the right of the pad if you managed to do so?! Thanks

---

### Post by william2018 on 2013-07-10
@mladenkovacevic,

As far as I am concerned, huion tablets are best compatible with Windows XP/ Vista / 7 / 8 or Mac, instead of Linux.
With regard to the drawing tools, it's better using SAI.
Only under this condition can the tablet perform it's best function.
Hope this can help you and other people with similar problem as well.

Product Page:
[http://www.huiontablet.com/product/product.php?sku=1004](http://www.huiontablet.com/product/product.php?sku=1004)

---

### Post by kcpr on 2013-09-10
That's the answer I got from Huion - I asked about the drivers for Linux generally:
"Kindly inform you that we have the driver for Linux, but we           didn't post it online because it's a little bit complicated in           installing.
          
          Our driver has been successfully run on Ubuntu 12.04,RHEL 6.2.
          Here's the Huion Source Code
          [http://www.huiontablet.com/developer/huiontablet.c](http://www.huiontablet.com/developer/huiontablet.c)
          
          Huion Linux Driver Install Guide.
          [http://www.huiontablet.com/developer/huion_guide.txt](http://www.huiontablet.com/developer/huion_guide.txt)
          
           We offer the Linux driver source code for Huion tablet, and we also offer a guide to tell our client how to integrate it into Linux kernel.            
           Install driver in Linux is more complex than in Windows,so it is a little difficult for common consumer to install himself.Our driver has            
          been successfully run on Ubuntu 12.04,RHEL 6.2.".

---

### Post by Cristiano_Pruneri on 2014-05-13
There is a "Huion Driver" in the Digimend project. It works pretty fine and installation is pretty simple, really (one just have to do "make" and "sudo make install" in the directory where he stored the sources).

This driver allows for the full spatial resolution of the tablet (way finer than 2047, and it shows when you work at low zoom).

Unfortunately, I do not know how much configurable it is... 

By the way, the digimend Huion driver coexist without problems with the driver for Wacom, too...

---

