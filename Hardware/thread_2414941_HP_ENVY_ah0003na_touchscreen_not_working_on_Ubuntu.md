---
title: "HP ENVY ah0003na touchscreen not working on Ubuntu 18.04"
date: 2019-03-17
forum: Hardware
---

### Post by sanctimonious on 2019-03-17
Hi all,

Ubuntu does not recognise/activate the touch screen on HP Envy AH0003na.

This is the output of xinput:

```
&#9121; Virtual core pointer                      id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                id=4    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                id=11   [slave  pointer  (2)]
&#9123; Virtual core keyboard                     id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard               id=5    [slave  keyboard (3)]
    &#8627; Power Button                              id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                 id=7    [slave  keyboard (3)]
    &#8627; Video Bus                                 id=8    [slave  keyboard (3)]
    &#8627; HP Wide Vision HD Camera: HP Wi           id=9    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard              id=10   [slave  keyboard (3)]
    &#8627; HP Wireless hotkeys                       id=12   [slave  keyboard (3)]
    &#8627; HP WMI hotkeys                            id=13   [slave  keyboard (3)]

```
This is the output of lsusb:

```
Bus 002 Device 002: ID 0781:5591 SanDisk Corp. 
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 8087:0a2a Intel Corp. 
Bus 001 Device 002: ID 04f2:b655 Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

Any ideas?

---

