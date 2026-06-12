---
title: "ELAN Touchscreen not waking from suspend"
date: 2015-09-15
forum: Hardware
---

### Post by ojdon on 2015-09-15
I have a Lenovo Flex 10 which has been running 15.04 with Linux 4.2 Kernel due to having better Baytrail support.

The only issue I have remaining is that there are a few USB devices that are not waking up from resuming from suspend, including the ELAN Touchscreen. Here is a few logs, that I hope are relevant:
lsbusb **before** suspend:
```

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 05e3:0610 Genesys Logic, Inc. 4-port hub
Bus 001 Device 003: ID 13d3:5614 IMC Networks 
Bus 001 Device 002: ID 04f3:024b Elan Microelectronics Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```
lsbusb **after** suspend:
```

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```
xinput list **before** suspend:
```

&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; ELAN Touchscreen                        	id=10	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=14	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=9	[slave  keyboard (3)]
    &#8627; Lenovo EasyCamera                       	id=11	[slave  keyboard (3)]
    &#8627; Ideapad extra buttons                   	id=12	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=13	[slave  keyboard (3)]

```
xinput **after** suspend:
```

Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=14	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=9	[slave  keyboard (3)]
    &#8627; Ideapad extra buttons                   	id=12	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=13	[slave  keyboard (3)]

```

I've tried a few things however only a reboot seems to resolve the issue. Any ideas on how to re-enable them after suspending the laptop?

---

### Post by ojdon on 2016-01-25
I'm still having this issue, anyone know of any potential solutions?

---

### Post by Vasiliy_Sazonov on 2016-02-07
Hi Ojdon!

 I have the same issue as well, My small laptop is lenovo flex 10 also.
 Unfortunatelly I haven't find solution yet.

---

