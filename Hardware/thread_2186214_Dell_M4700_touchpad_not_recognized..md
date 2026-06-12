---
title: "Dell M4700 touchpad not recognized."
date: 2013-11-06
forum: Hardware
---

### Post by DawgMan on 2013-11-06
I have a Dell M4700 with Ubuntu 12.04.   In All Settings - Mouse and Touchpad it does not show a touchpad.  When I boot of the live USB it does show the touchpad.  My touchpad works but it's real flaky.

How can I make ubuntu re-scan devices and load the proper drivers?  I tried loading synaptiks touchpad management but that did not help.

Any help would be great.

Thanks

---

### Post by DawgMan on 2013-11-19
OK,  I installed this copy of Ubuntu from an iso that I downloaded from Dell. Here is the result of the xinput list

&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; PS/2 Generic Mouse                      	id=11	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=9	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=10	[slave  keyboard (3)]
    &#8627; Dell WMI hotkeys                        	id=12	[slave  keyboard (3)]


It sees the touchpad as a PS/2 Generic Mouse


Here is the xinput list from when I boot from the Live USB downloaded from ubuntu

&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; DualPoint Stick                         	id=11	[slave  pointer  (2)]
&#9116;   &#8627; AlpsPS/2 ALPS DualPoint TouchPad        	id=12	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=9	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=10	[slave  keyboard (3)]
    &#8627; Dell WMI hotkeys                        	id=13	[slave  keyboard (3)]

This shows the touchpad as an AlpsPS/2 ALPS DualPoint TouchPad.

I found this post [http://ubuntuforums.org/showthread.php?t=2186739&highlight=touchpad+dell](http://ubuntuforums.org/showthread.php?t=2186739&highlight=touchpad+dell) at the end the touchpad gets fixed.  They have an Elantech Touchpad and appears to have installed a driver for Elantech. 

My question is: can I do this?  If so, where do I wget the file for an Alps touchpad?

Dan

---

