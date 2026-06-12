---
title: "Touchpad Problems on HP dm4-2165dx"
date: 2011-10-09
forum: Hardware
---

### Post by paulbdavis on 2011-10-09
I just got an HP dm4-2165dx and I am running Ububtu 11.04 (64 bit)

xinput list tells me


```
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; PS/2 Mouse                              	id=11	[slave  pointer  (2)]
&#9116;   &#8627; AlpsPS/2 ALPS GlidePoint                	id=12	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; HP Truevision HD                        	id=9	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=10	[slave  keyboard (3)]
    &#8627; HP WMI hotkeys                          	id=13	[slave  keyboard (3)]
```

and /proc/bus/input/devices tells me this about it

```
I: Bus=0011 Vendor=0002 Product=0008 Version=7326
N: Name="AlpsPS/2 ALPS GlidePoint"
P: Phys=isa0060/serio4/input0
S: Sysfs=/devices/platform/i8042/serio4/input/input8
U: Uniq=
H: Handlers=mouse1 event8 
B: PROP=0
B: EV=b
B: KEY=420 70000 0 0 0 0
B: ABS=1000003
```

The trackpad itself works, and there is a tab for trackpad in the mouse preferences, but any changes made there are not reflected in the trackpad's behavior.

This includes turning off the trackpad while typing and turning off tap to click. Two finger scrolling and horizontal scrolling are also not activating even though they are showing up as options

I have tried searching, but have not been able to find anything that works/anything that has been updated in the past few years.

Thanks in advance

---

### Post by paulbdavis on 2011-10-10
I've tried to use synaptics, but I can't seem to figure it out, and anything I have found online is pretty outdated

---

### Post by paulbdavis on 2011-10-10
I could also use help in focusing my search, if there is more information I should be looking for to help define my problem better that would be good too.

---

