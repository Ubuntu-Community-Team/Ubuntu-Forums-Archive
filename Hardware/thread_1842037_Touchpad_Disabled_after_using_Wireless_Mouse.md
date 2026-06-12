---
title: "Touchpad Disabled after using Wireless Mouse"
date: 2011-09-10
forum: Hardware
---

### Post by LiteDrive on 2011-09-10
I currently dual-boot both Windows 7 and Ubuntu 11.04. My touchpad is disabled for both of these, and I've gone through the touchpad troubleshooting guide in the ubuntu documentation. Unfortunately, that hasn't helped much. I've also tried installing the Touchpad Indicator program, which hasn't helped either.

My xinput list gives the following output:

```
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; HID 04d9:0499                           	id=11	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=13	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=9	[slave  keyboard (3)]
    &#8627; 1.3M HD WebCam                          	id=10	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=12	[slave  keyboard (3)]
```

Is there anything I can use to debug this, or some bash command I can run to reinstall the drivers?

Please help, and thanks in advance for any replies.

---

