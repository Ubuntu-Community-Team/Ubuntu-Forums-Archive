---
title: "Rotation situation with N-trig on a hp tx-2"
date: 2011-12-01
forum: Hardware
---

### Post by zush on 2011-12-01
I'm having trouble with xinput set-prop commands if I for example put in a xinput set-prop "N-Trig Touchscreen" "Device Enabled" 0

I get the error 


Warning: There are multiple devices matching 'N-Trig Touchscreen'.
To ensure the correct one is selected, please use the device ID, or prefix the
device name with 'pointer:' or 'keyboard:' as appropriate.

unable to find device N-Trig Touchscreen

same thing happens if I want to use a transformation matrix on one of the devices
And no wonder cause my xinput -list looks like this:


> &#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Logitech USB-PS/2 Optical Mouse         	id=10	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=15	[slave  pointer  (2)]
&#9116;   &#8627; N-Trig Pen stylus                       	id=12	[slave  pointer  (2)]
&#9116;   &#8627; N-Trig Pen pad                          	id=18	[slave  pointer  (2)]
&#9116;   &#8627; N-Trig Pen stylus                       	id=20	[slave  pointer  (2)]
&#9116;   &#8627; N-Trig Pen eraser                       	id=21	[slave  pointer  (2)]
&#9116;   &#8627; N-Trig Pen pad                          	id=22	[slave  pointer  (2)]
&#9116;   &#8627; N-Trig Touchscreen                      	id=23	[slave  pointer  (2)]
&#9116;   &#8627; N-Trig Touchscreen                      	id=19	[slave  pointer  (2)]
&#9116;   &#8627; N-Trig Pen eraser    

This is a snippet but you see the issue, two touchscreen devices (just like 2 of every other device)

I've managed to work around it by using the id numbers in xinput.
The problem with this is that my touchscreen is rather buggy in that it quite often restarts itself and then xinput assigns it a different Id number so all my touchscreen toggle/rotation scripts become useless. Rebooting fixes this but I'm really looking for a more elegant solution.

So would there be a way to either "grab" the current ID number from xinput or maybe even? delete one of the touchscreen devices (when I use the Id numbers to disable the devices one disables touch one doesn't do anything). Would love to get some help on this. 

Thanks.

---

