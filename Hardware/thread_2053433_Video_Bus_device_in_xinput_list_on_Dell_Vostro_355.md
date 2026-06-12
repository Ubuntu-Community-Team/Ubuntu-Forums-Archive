---
title: "Video Bus device in xinput list on Dell Vostro 3550"
date: 2012-09-05
forum: Hardware
---

### Post by zuker on 2012-09-05
Hi all!
I would like to know what this device
```
Video Bus id=8 [slave  keyboard (3)]
```
in my xiniput --list stands for
full output:
```

&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; AlpsPS/2 ALPS DualPoint TouchPad        	id=13	[slave  pointer  (2)]
&#9116;   &#8627; DualPoint Stick                         	id=14	[slave  pointer  (2)]
&#9116;   &#8627; Bluetooth Laser Travel Mouse            	id=16	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=9	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=10	[slave  keyboard (3)]
    &#8627; Laptop_Integrated_Webcam_FHD            	id=11	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=12	[slave  keyboard (3)]
    &#8627; Dell WMI hotkeys                        	id=15	[slave  keyboard (3)]
    &#8627; 00:06:F5:EF:F5:FC                       	id=17	[slave  keyboard (3)]
    **&#8627; Video Bus                               	id=8	[slave  keyboard (3)]**


```

This device is causing windows and cursor flickering and generates "^@" sequence in console, unless disabled (xinput set-prop 8 "Device Enabled" 0)

Thanks!

---

### Post by zuker on 2012-09-05
Bump!

---

### Post by zuker on 2012-09-06
Bump!!

---

### Post by zuker on 2012-09-06
Desperate bump!

---

### Post by zuker on 2012-09-07
Bump!

---

### Post by zuker on 2012-09-08
Bump!

---

### Post by zuker on 2012-09-10
_**Bump!**_

---

