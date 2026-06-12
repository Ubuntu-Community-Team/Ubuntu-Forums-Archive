---
title: "Wacom Intuos 2 tablet stops working after unplugged and replugged"
date: 2013-01-27
forum: Hardware
---

### Post by cb2 on 2013-01-27
Hi, I recently got an old Wacom Intuos 2 tablet and am using it with a laptop (Lenovo W520, i7 processor) with Ubuntu 12.04 (64b).  My xorg version is 1.11.3.

My tablet works fine when first plugged in, but if I unplug it and replug it, then it stops working and the only way to get it to start working again is by rebooting.  More specifically, the lights on the tablet come on when I move the pen, but it isn't recognized as input--nothing changes on the screen.

I looked around online and saw a lot of cases where this wasn't solved or solved via hotplugging, but is that only applicable to earlier versions of xorg?

Sorry if there's an obvious fix here--I'm an ubuntu newbie and am pretty stuck.

Here's what I've tried:
--I've updated all the drivers--nothing's changed.
--modprobe does nothing.
--lsmod does show wacom:
    Module                  Size  Used by
    pci_stub               12622  1 
    vboxpci                23237  0 
    ... 
    joydev                 17693  0 
    wacom                  53300  0 
    arc4                   12529  2 
    ...

--lsusb shows wacom:
lsusb | grep Wacom
Bus 001 Device 007: ID 056a:0042 Wacom Co., Ltd Intuos2 6x8

--xinput shows wacom:
xinput list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; stylus                                  	id=6	[slave  pointer  (2)]
&#9116;   &#8627; eraser                                  	id=7	[slave  pointer  (2)]
&#9116;   &#8627; cursor                                  	id=8	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=14	[slave  pointer  (2)]
&#9116;   &#8627; TPPS/2 IBM TrackPoint                   	id=16	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=9	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=10	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=11	[slave  keyboard (3)]
    &#8627; Integrated Camera                       	id=12	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=13	[slave  keyboard (3)]
    &#8627; ThinkPad Extra Buttons                  	id=15	[slave  keyboard (3)]

--results from xsetwacom:
xsetwacom list
stylus                          	id: 6	type: STYLUS    
eraser                          	id: 7	type: ERASER    
cursor                          	id: 8	type: CURSOR   

I'm just stuck...do you have any suggestions?  
Thanks so much!

---

