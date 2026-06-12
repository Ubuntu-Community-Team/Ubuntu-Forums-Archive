---
title: "Trackpad not detected"
date: 2015-01-25
forum: Hardware
---

### Post by jass_productions on 2015-01-25
Trying to get a trackpad detected. Output of  grep -i touchpad /var/log/Xorg.0.log is:   [    37.078] (**)    : Applying InputClass "evdev touchpad catchall"  [    37.078] (**)    : Applying InputClass "touchpad catchall"  [    37.097] (--) synaptics:    : touchpad found  [    37.108] (II) XINPUT: Adding extended input device "   " (type: TOUCHPAD, id 14)  [    37.109] (--) synaptics:    : touchpad found  [    37.111] (**)    : Ignoring device from InputClass "touchpad ignore duplicates"   and the output of xinput list is:   &#9121; Virtual core pointer                    	 id=2	[master pointer  (3)]  &#9116;   &#8627; Virtual core XTEST pointer   id=4	[slave  pointer  (2)] &#9116;    &#8627; Logitech Unifying Device. Wireless PID:4009	id=10	[slave  pointer  (2)]  &#9116;   &#8627; SIGMACHIP USB Keyboard  id=12	[slave  pointer  (2)] &#9116;   &#8627;                                         	        id=14	[slave  pointer  (2)]  &#9123; Virtual core keyboard                  id=3	[master keyboard (2)]      &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]      &#8627; Power Button                            	id=6	[slave  keyboard (3)]      &#8627; Video Bus                               	id=7	[slave  keyboard (3)]      &#8627; Power Button                            	id=8	[slave  keyboard (3)]      &#8627; Sleep Button                            	id=9	[slave  keyboard (3)]      &#8627; SIGMACHIP USB Keyboard   id=11	[slave  keyboard (3)]      &#8627; HD WebCam                              id=13	[slave  keyboard (3)]      &#8627; AT Translated Set 2 keyboard            	id=15	[slave  keyboard (3)]      &#8627; Acer WMI hotkeys                   id=16	[slave  keyboard (3)]    It looks like its been assigned id=14, but it shows a blank line beside that id.     specs: Acer Aspire E15 E5-521-85EX

---

