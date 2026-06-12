---
title: "Huion H420 not working"
date: 2016-12-12
forum: Hardware
---

### Post by ayylmao25 on 2016-12-12
I had the graphics tablet working earlier this morning (from a fresh install of Ubuntu) and everything was in order and working. Then I came home today to find that the tablet wouldn't respond, but the light showed when I tried to draw. I plugged the tablet in and out again, with no avail, and then reinstalled the drivers from digimend, but that didn't help either. My next port of call was to look at xinput and lsusb. The tablet does not show up at all in either:
```

x@Z87-HD3:~$ xinput
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; PS/2+USB Mouse                              id=9    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Metadot - Das Keyboard Das Keyboard         id=10    [slave  keyboard (3)]
    &#8627; Metadot - Das Keyboard Das Keyboard         id=11    [slave  keyboard (3)]
    &#8627; USB2.0 PC CAMERA                            id=12    [slave  keyboard (3)]

```
and
```

x@Z87-HD3:~$ lsusb
Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 2109:0812 VIA Labs, Inc. VL812 Hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 010: ID 256c:006e  
Bus 003 Device 005: ID 1908:2310 GEMBIRD 
Bus 003 Device 003: ID 058f:6362 Alcor Micro Corp. Flash Card Reader/Writer
Bus 003 Device 006: ID 24f0:0140  
Bus 003 Device 004: ID 1267:0210 Logic3 / SpectraVideo plc LG Optical Mouse 3D-310
Bus 003 Device 002: ID 2109:2812 VIA Labs, Inc. VL812 Hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```
I have tried every usb port on the computer, but it still won't show up, let alone respond. I tested the tablet in a windows computer with the drivers, and it works with pressure (but the laptop is so slow it's impossible to use it for the work I do).
What might be wrong and most importantly, how can I fix this?

EDIT: I think that 256c:006e is the tablet. It's detected by the computer, but isn't an input. The right driver is loaded (hid-uclogic.ko) from digimend kernel drivers 6. I also ran make and make install in the directory before I did that.

---

