---
title: "Disabled touch screen drivers restart automatically?"
date: 2017-07-10
forum: Hardware
---

### Post by Matt_Boling on 2017-07-10
Hello!
On my laptop, my touch screen is rather bugged up and annoying - as in, it will act as if something is touching the screen when nothing is. So, as a solution, I have resorted to 
"xinput -disable 10"
as my means of disabling my touch screen.
xinput yields the following:
"&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=12	[slave  pointer  (2)]
&#9116;   &#8627; eGalax Inc. eGalaxTouch EXC3000-0367-44.01.00	id=10	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; HP Webcam                               	id=9	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=11	[slave  keyboard (3)]
    &#8627; HP WMI hotkeys                          	id=13	[slave  keyboard (3)]
    &#8627; HP Wireless hotkeys  "

However, within a few seconds (at a minimum, 15 seconds, a couple minutes at a maximum), these touch screen drivers automatically get re-enabled.
I didn't have this problem with previous versions of Ubuntu, as it seems there is an annoying process which is checking to see if something gets disabled and automatically re enables it.

Does anybody have a solution to this problem? Is there a way to delete these drivers?
 It is really annoying to be just browsing the internet and then it gets zoomed in like 800 % for no reason, and then I have to fight my computer to get into terminal to execute my xinput command.

Thanks,
-Matt

---

