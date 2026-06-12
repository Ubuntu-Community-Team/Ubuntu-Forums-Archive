---
title: "Mouse randomly going crazy with touchscreen computer"
date: 2015-07-19
forum: Hardware
---

### Post by nathanhurley on 2015-07-19
Hi. This issue is driving me crazy, so any help would be highly appreciated.

Well I have a real piece of crap computer (dell Studio One) all in one computer with touchscreen. This is the only computer the mouse goes crazy randomly. I have tried a different mouse to no avail. I tried a few other posts recommendations to no avail. 

Also, how do I disable touchscreen? Could this be the issue? I do not use it.

I am using Lubuntu 15.04 freshly installed.

---

### Post by Shivakumar_Gurumurthy on 2015-07-30
The issue is with the touch screen. It works initially and suddenly the mouse goes crazy.

you can list input devices with xinput list command. For me touch screen ID is 12. Disable the same by typing "xinput disable 12". I created a shortcut for the command.

shivakumar@shivakumar-Inspiron-7347:~$ xinput list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; ELAN Touchscreen Pen                    	id=11	[slave  pointer  (2)]
**&#9116;   &#8627; ELAN Touchscreen                        	id=12	[slave  pointer  (2)]**
&#9116;   &#8627; DLL0674:00 06CB:75DB UNKNOWN            	id=13	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=15	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=9	[slave  keyboard (3)]
    &#8627; Integrated_Webcam_HD                    	id=10	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=14	[slave  keyboard (3)]
    &#8627; Dell WMI hotkeys                        	id=16	[slave  keyboard (3)]

---

