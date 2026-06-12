---
title: "Ubuntu touchpad only works when pressing down"
date: 2018-12-27
forum: Hardware
---

### Post by Mathurin1968 on 2018-12-27
HP Envy laptop with Ubuntu 18 BUT the touchpad has stopped working... not sure, probably something I did somewhere. 

The pointer doesn't move at all unless you press down on the pad then drag the pointer - no pressing on the touchpad.  Just sliding your finger on the touchpad doesn't seem to work anymore.  

I installed xserver-xorg-input-synaptics but nothing...

Anyone else seen this?  It works fine with a mouse plugged into it, but, I can't stand when something doesn't work right.  

Thanks!!

---

### Post by #&amp;thj^% on 2018-12-27
To list all device's use:
This is how mine shows:
```
xinput list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Logitech K780                           	id=9	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=12	[slave  pointer  (2)]
&#9116;   &#8627; TPPS/2 IBM TrackPoint                   	id=13	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=8	[slave  keyboard (3)]
    &#8627; Integrated Camera: Integrated C         	id=10	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=11	[slave  keyboard (3)]
    &#8627; ThinkPad Extra Buttons                  	id=14	[slave  keyboard (3)]
    &#8627; Logitech K780                           	id=15	[slave  keyboard (3)]


```

Ubuntu 18.04 comes with libinput touchpad driver by default and the OS is missing Synaptics touchpad driver.
To see if installed use:
```

apt policy xserver-xorg-input-synaptics
```
if it shows as not installed use:
```
sudo apt install xserver-xorg-input-synaptics
```
**EDIT: Sorry I just flat missed this:** "I installed xserver-xorg-input-synaptics but nothing...
"

---

### Post by Mathurin1968 on 2018-12-28
Hah. no worries!  I appreciate the suggestion.  Yeah, I think I've messed something up somewhere.

---

### Post by liaata on 2018-12-28
Sorry if this sounds strange, but there is a keyboard combination to turn the touchpad off. 
Happened to me as well haha

---

