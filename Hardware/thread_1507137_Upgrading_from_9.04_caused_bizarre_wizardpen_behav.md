---
title: "Upgrading from 9.04 caused bizarre wizardpen behaviour."
date: 2010-06-11
forum: Hardware
---

### Post by Spummy on 2010-06-11
Hey, I'm using a Genius G-Note 7000 tablet, which I working fine using the wizardpen driver with my 9.04 install. After the release of 10.04, I decided to upgrade.

 Since then proximity movement for the tablet suffers a bizarre error. When I press the pen against the surface, proximity movement dies. If I take the pen far enough away from the surface, then bring it back, it recognizes proximity movement again. But, this will cause it to draw a solid line from the place I pulled the pen away from to where I returned the pen. Making the tablet useless for graphics purposes.

Has anyone seen this before? Any help is most welcome.

Thanks for your time.

---

### Post by Favux on 2010-06-11
Hi Spummy,

Welcome to Ubuntu forums!

Have you tried the latest WizardPen driver from DoctorMo yet?:  [https://launchpad.net/~doctormo/+archive/xorg-wizardpen](https://launchpad.net/~doctormo/+archive/xorg-wizardpen)  Just download the appropriate deb and dbl click on it to install.

Hope this helps.

---

### Post by Spummy on 2010-06-11
Yeah, I tried yesterday before posting. And saw no change in behaviour.

---

### Post by Favux on 2010-06-12
Hi Spummy,

That's the 0.7.3-1 dated 4-16-10?

If so try reinstalling the deb and rebooting.

If that doesn't work then let's see what Xinput sees.  In a terminal copy and paste:
```
xinput --list
```
We also want to look at the 90-wizardpen.conf located at /usr/lib/X11/xorg.conf.d/.
Also at Xorg.0.log located at /var/log/.  To compress it right click on it and Created Archive.  To post use Manage attachments below.

---

### Post by Spummy on 2010-06-12
Hey. I'm not quite sure how to check the date.

xinput --list returns:

```
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; USB Optical Mouse                       	id=8	[slave  pointer  (2)]
&#9116;   &#8627;                 Digital Ink Pad         	id=9	[slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation        	id=11	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Power Button                            	id=7	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=10	[slave  keyboard (3)]

```

I'm pretty sure it's Didgital Inkpad.

Oddly I have no 90-wizard.conf, but I do have a 70-wizard-conf in that dir:

```
Section "InputClass"
   Identifier "wizardpen"
   MatchIsTablet "on"
   MatchDevicePath "/dev/input/event*"
   MatchVendor "UC-LOGIC|KYE Systems|Ace Cad"
   Driver "wizardpen"
EndSection
Section "InputClass"
   Identifier "wizardpen ignore mouse dev"
   MatchIsTablet "on"
   MatchDevicePath "/dev/input/mouse*"
   MatchVendor "UC-LOGIC|KYE Systems|Ace Cad"
   Driver ""
EndSection

```

I'll get that log archive for ya.

---

### Post by Favux on 2010-06-12
Hi Spummy,

The Xorg.0.log shows that the evdev driver has your tablet which is why it is behaving weird.

We may have to look at udevadm info. to find the right thing for the MatchVendor line, but let's see if what xinput is listing works.  So in both snippets/sections of the 70-wizard-conf change this line:
```
   MatchVendor "UC-LOGIC|KYE Systems|Ace Cad"

```
to
```
   MatchVendor "UC-LOGIC|KYE Systems|Ace Cad|Digital Ink Pad"

```
and see if that does the trick.

I'm guessing Digital Ink Pad is the Vendor/OEM.  Since I seem to remember iVista Tablet was the first one with the paper clipboard Digital Ink Pad that may be them.  And now a lot of manufacturers, like Genius, rebrand them.

---

### Post by Spummy on 2010-06-12
Hey again. Tried both 
MatchVendor "UC-LOGIC|KYE Systems|Ace Cad|Digital Ink Pad" and 
MatchVendor "UC-LOGIC|KYE Systems|Ace Cad|                Digital Ink Pad" (Tried the second one because it always returned it like that.) And saw no difference in behaviour.

So what udevadm command do I have to run? 

Thanks in advance for helping. :)

---

### Post by Favux on 2010-06-12
I was hoping we'd get lucky, oh well.

This is the command:
```
udevadm info --export-db > $HOME/udevadm-info.txt
```
So the file udevadm-info.txt will be created in your username directory.  And you can compress and attach it like you did with Xorg.0.log.

---

### Post by Spummy on 2010-06-12
K, here it is.

---

### Post by Favux on 2010-06-12
It's saying:
```
ID_VENDOR_ID=172f
ID_MODEL_ID=0027
ID_MODEL=Digital_Ink_Pad
```
So keeping the MatchVendor line let's try:
```
   MatchVendor "UC-LOGIC|KYE Systems|Ace Cad|172f:0027"
```

---

### Post by Spummy on 2010-06-12
Hey. Unfortunantly it's still the same behaviour. :(

Is the second Driver setting in the the 70-wizardpen.conf suppose to be ""?

---

### Post by Favux on 2010-07-03
Hi Spummy,

> Is the second Driver setting in the the 70-wizardpen.conf suppose to be ""? 
Yes that's apparently so a spurious node is matched but given no driver.

Could you give me a summary of where you are (what changes you've made) and repeat the 'xinput --list' and Xorg.0.log.

---

### Post by Spummy on 2010-07-03
Hey. I havn't done anything since, so the only change I think is I'm using "MatchVendor "UC-LOGIC|KYE Systems|Ace Cad|172f:0027"" 

Here's Xinput --list again
```
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627;                 Digital Ink Pad         	id=8	[slave  pointer  (2)]
&#9116;   &#8627; USB Optical Mouse                       	id=9	[slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation        	id=11	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Power Button                            	id=7	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=10	[slave  keyboard (3)]

```

And the xorg.0.log.

Thanks again man.

---

### Post by Favux on 2010-07-03
OK, still no sign of the wizardpen driver.

Try:
```
MatchVendor "UC-LOGIC|KYE Systems|Ace Cad|Digital_Ink_Pad"
```

---

### Post by Spummy on 2010-07-03
Still no change. D:

---

### Post by Favux on 2010-07-03
I wish we had some way to verify the wizardpen driver installed correctly and is active.  When we change the MatchVendor line(s) you're changing both of them in the 70-wizardpen.conf, correct?

---

### Post by Spummy on 2010-07-03
Yep.

---

### Post by Favux on 2010-07-03
Alright, what if we try this:
```
Section "InputClass"
   Identifier "wizardpen"
   MatchIsTablet "on"
   MatchDevicePath "/dev/input/event4"
#   MatchVendor "UC-LOGIC|KYE Systems|Ace Cad"
   Driver "wizardpen"
EndSection
Section "InputClass"
   Identifier "wizardpen ignore mouse dev"
   MatchIsTablet "on"
   MatchDevicePath "/dev/input/mouse*"
   MatchVendor "UC-LOGIC|KYE Systems|Ace Cad"
   Driver ""
EndSection
```
The idea is to "force" a match on event4, which we know is the tablet, and see if the wizardpen driver picks it up.  We'll want to look at 'xinput --list' and Xorg.0.log again.

---

### Post by Spummy on 2010-07-03
Well, it caused a notable change in behaviour. Using the tablet forces the cursor to the upper-left corner and cannot be moved with it.

xinput --list:

```
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627;                 Digital Ink Pad         	id=8	[slave  pointer  (2)]
&#9116;   &#8627; USB Optical Mouse                       	id=9	[slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation        	id=11	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Power Button                            	id=7	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=10	[slave  keyboard (3)]

```

---

### Post by Favux on 2010-07-03
Got it!
> config/udev: Adding input device                 Digital Ink Pad (/dev/input/event4)
(**)                 Digital Ink Pad: Applying InputClass "evdev pointer catchall"
(**)                 Digital Ink Pad: Applying InputClass "evdev tablet catchall"
(**)                 Digital Ink Pad: Applying InputClass "wizardpen"
(II) LoadModule: "wizardpen"
(II) Loading /usr/lib/xorg/modules/input/wizardpen_drv.so
(II) Module wizardpen: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 0.7.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 7.0
(**) Option "Device" "/dev/input/event4"
(--)                 Digital Ink Pad: MaxX:136170139 MaxY:1364514 MaxZ:1023
(--)                 Digital Ink Pad: aspect ratio:1.33:1
(**)                 Digital Ink Pad is in absolute mode
(**)                 Digital Ink Pad: TopX not set, defaulting to "5%"
(**)                 Digital Ink Pad: TopY not set, defaulting to "5%"
(**)                 Digital Ink Pad: BottomX not set, defaulting to "95%"
(**)                 Digital Ink Pad: BottomY not set, defaulting to "95%"
(II)                 Digital Ink Pad: ScreenX = 1024, ScreenY = 768
(**)                 Digital Ink Pad: TopX                   = 6808506
(**)                 Digital Ink Pad: TopY                   = 68225
(**)                 Digital Ink Pad: BottomX                = 129361632
(**)                 Digital Ink Pad: BottomY                = 1296288
(**)                 Digital Ink Pad: TopZ    (min pressure) = 0
(**)                 Digital Ink Pad: BottomZ (max pressure) = 1023
(**)                 Digital Ink Pad: always reports core events
(II) XINPUT: Adding extended input device "                Digital Ink Pad" (type: WizardPen Tablet)
(II)                 Digital Ink Pad Increment: 1776
(II) config/udev: Adding input device                 Digital Ink Pad (/dev/input/mouse1)
(II) No input driver/identifier specified (ignoring)
Arrow at upper left means xinput isn't getting proper signals.  But we finally see the wizardpen driver.

If we can now get it working we need to identify a better match.

---

### Post by Spummy on 2010-07-04
Okay. What does that mean we have to do now?

---

### Post by Favux on 2010-07-04
Do you have the settings from the previous releases when it worked?  Like the xorg.conf or wizardpen.fdi you were using?

---

### Post by Spummy on 2010-07-04
Ahh. K. I think I do somewhere. I'll report back if success/i get lost. Thank's for the help!

---

