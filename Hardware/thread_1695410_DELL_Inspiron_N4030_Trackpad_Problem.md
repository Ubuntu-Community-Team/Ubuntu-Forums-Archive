---
title: "DELL Inspiron N4030 Trackpad Problem"
date: 2011-02-25
forum: Hardware
---

### Post by but2002 on 2011-02-25
As the topic title states, I have a Dell Inspiron N4030 laptop, and the trackpad is getting detectd as a standard PS/2 mouse, however the laptop's "disable trackpad" button brings up the notification window saying trackpad has been disabled, it's still enabled.

I also can use side-scrolling, or any other features without Ubuntu recognizing it.

Here's the output from xinput

```
xbarry@Barry-Laptop-Ubuntu:~$ xinput list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Receiver                   	id=11	[slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Receiver                   	id=12	[slave  pointer  (2)]
&#9116;   &#8627; PS/2 Generic Mouse                      	id=14	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=9	[slave  keyboard (3)]
    &#8627; Laptop_Integrated_Webcam_0.3M           	id=10	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=13	[slave  keyboard (3)]
    &#8627; Dell WMI hotkeys                        	id=15	[slave  keyboard (3)]

```

What should I do?

---

### Post by but2002 on 2011-03-05
I'm bumping this because I still can't figure this out, and it is driving me absolutely nuts.

---

### Post by but2002 on 2011-04-06
I still don't know what's going on.  Could I please get some help here?

---

### Post by but2002 on 2011-04-13
Please help me!  Linux offers me everything I need (Except for netflix) and it runs so much faster for me on this laptop than Windows does.  The only thing keeping me from it is this stupid touchpad not working right, and I have no idea what to do.  Help?  D:

---

### Post by but2002 on 2011-05-05
This issue is closed now.  I upgraded to Natty and the trackpad works again

---

### Post by jamesisin on 2012-02-28
I take it you didn't get it to work in older versions?  I have the same lappy running 10.04 and it also thinks it's a regular mouse.

Any suggestions short of upgrading the OS (which I certainly won't do until 12.04 for various reasons)?

---

