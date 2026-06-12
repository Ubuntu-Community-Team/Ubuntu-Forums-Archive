---
title: "Keyboard Not Working"
date: 2018-07-11
forum: Hardware
---

### Post by eldstal on 2018-07-11
I recently purchased an inexpensive mechanical keyboard but it Ubuntu does not seem to recognize the keystrokes. Oddly the volume control on the keyboard works fine. 

I ran xinput to see if the keyboard was recognized and this is what i got:

```

$ xinput list&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Optical Mouse              	id=9	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=15	[slave  pointer  (2)]
&#9116;   &#8627; TPPS/2 IBM TrackPoint                   	id=16	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=8	[slave  keyboard (3)]
    &#8627; Integrated Camera: Integrated C         	id=10	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=14	[slave  keyboard (3)]
    &#8627; ThinkPad Extra Buttons                  	id=17	[slave  keyboard (3)]
    &#8627; Logitech USB Keyboard                   	id=11	[slave  keyboard (3)]
    &#8627; Logitech USB Keyboard                   	id=12	[slave  keyboard (3)]
    &#8627; EPICGEAR DeFiant Keyboard               	id=13	[slave  keyboard (3)]
    &#8627; EPICGEAR DeFiant Keyboard               	id=18	[slave  keyboard (3)]
    &#8627; EPICGEAR DeFiant Keyboard               	id=19	[slave  keyboard (3)]

```

As you can see it is recognizing it as a keyboard but it is not accepting keystrokes. Since there is not a linux driver available is there some way I can map the keys manually so that this keyboard becomes usable?

---

