---
title: "Lenovo X230 Tablet Wacom Fingertouch problems"
date: 2015-10-17
forum: Hardware
---

### Post by pjotr-van-baarle on 2015-10-17
Hi all,

I recently acquired a X230 tablet laptop and seem to be having some problems with the Wacom drivers. The pen works fine, I can rotate the screen and use the pen to type on the virtual keyboard etc. Fingertouch on the other hand (<-haha) seems to generate some problems. I can touch the screen to open apps and such, but typing on the virtual keyboard does not work. It just does not seem to register the touch. Also, it's calibrated perfectly in the standard screen setting, but when I rotate the screen the fingertouch calibration is still the other way around (which, needless to say, makes everything quite complicated). ~$ xinput list and xsetwacomlist show as below. Can anyone assist me? Thanks in advance.

Pjotr

~$ xinput list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Wacom ISDv4 E6 Pen stylus               	id=10	[slave  pointer  (2)]
&#9116;   &#8627; Wacom ISDv4 E6 Finger touch             	id=11	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=13	[slave  pointer  (2)]
&#9116;   &#8627; Wacom ISDv4 E6 Pen eraser               	id=15	[slave  pointer  (2)]
&#9116;   &#8627; TPPS/2 IBM TrackPoint                   	id=16	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=8	[slave  keyboard (3)]
    &#8627; Integrated Camera                       	id=9	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=12	[slave  keyboard (3)]
    &#8627; ThinkPad Extra Buttons                  	id=14	[slave  keyboard (3)] 



~$ xsetwacom list
Wacom ISDv4 E6 Pen stylus       	id: 10	type: STYLUS    
Wacom ISDv4 E6 Finger touch     	id: 11	type: TOUCH     
Wacom ISDv4 E6 Pen eraser       	id: 15	type: ERASER

---

