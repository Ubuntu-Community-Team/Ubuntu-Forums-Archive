---
title: "Ubuntu 10.10, mouse mappings incorrect?"
date: 2010-10-26
forum: Hardware
---

### Post by Bliepo32 on 2010-10-26
Recently, I installed Ubuntu 10.10 (I was using 10.04 before, but decided to do a clean install anyway). After some time, I noticed that using the middle mouse button in Firefox did not open a new tab, but instead just opened the link in the current tab.

After some research,I discovered that the middle mouse button acts the same as the left mouse button. I can use the middle mouse button to select text, switch Windows and so on.

I believe this to be caused by incorrect mouse mappings, but I don't know for certain. Anyway, here is some output of xinput:

```
something@something:~$ xinput list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=11	[slave  pointer  (2)]
&#9116;   &#8627; PS/2 Generic Mouse                      	id=12	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=8	[slave  keyboard (3)]
    &#8627; CKA7216                                 	id=9	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=10	[slave  keyboard (3)]
    &#8627; HP WMI hotkeys                          	id=13	[slave  keyboard (3)]
something@something:~$ xinput get-button-map "SynPS/2 Synaptics TouchPad"
1 2 3 4 5 6 7 8 9 10 11 12 
```

So is this caused by incorrect mouse mappings? If so, how do I correct them? If not, what might be the issue then?

---

### Post by Bliepo32 on 2010-10-26
Alright, I tried playing around a bit with the mouse mappings and I noticed that changing the mouse mapping for the left mouse button, changes the the mapping for the middle button as well.

So, if I remap the left mouse button to act like the right mouse button, then the middle mouse button will also act like the right mouse button.

---

### Post by Bliepo32 on 2010-10-26
It seems my problem was caused by a bug: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/612591](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/612591) The fix mentioned there fixed things for me :)

---

