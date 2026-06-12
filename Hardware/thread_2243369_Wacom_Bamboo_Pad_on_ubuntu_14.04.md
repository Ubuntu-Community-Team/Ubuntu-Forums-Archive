---
title: "Wacom Bamboo Pad on ubuntu 14.04"
date: 2014-09-08
forum: Hardware
---

### Post by spiros88 on 2014-09-08
Hello.
I have a Ubuntu 14.04.1 Ubuntu installation. I just received a [Bamboo Pad wireless]("http://www.wacom.com/en/us/everyday/bamboo-pad-wireless"), but Ubuntu does not recognize it. I plugged it in and it just does not work. Here are some commands:

```

$ lsusb | grep Wacom
Bus 002 Device 004: ID 056a:0319 Wacom Co., Ltd 

$ xinput list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Logitech Unifying Device. Wireless PID:1028	id=13	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=15	[slave  pointer  (2)]
&#9116;   &#8627; TPPS/2 IBM TrackPoint                   	id=17	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=8	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=9	[slave  keyboard (3)]
    &#8627; daskeyboard                             	id=10	[slave  keyboard (3)]
    &#8627; daskeyboard                             	id=11	[slave  keyboard (3)]
    &#8627; Integrated Camera                       	id=12	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=14	[slave  keyboard (3)]
    &#8627; ThinkPad Extra Buttons                  	id=16	[slave  keyboard (3)]

```

The "Wacom tablet" utility in the system settings says "No tablet detected". I searched around and found that it was apparently not yet supported by the wacom drivers. I would like to ask if things have changed in the meantime (or are about to change) or if somebody has some suggestions. Could an upgrade to Ubuntu 14.10 beta solve the issue? I don't mind having an unstable system.

---

