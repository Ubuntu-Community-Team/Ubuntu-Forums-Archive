---
title: "USB stick no longer recognised"
date: 2010-12-01
forum: Hardware
---

### Post by engine on 2010-12-01
Ubuntu 10.04, Maxell 8Gb USB stick

First thing this morning, wrote a text file in Gedit, plugged in USB stick and saved file: no apparent problems.

Shut down machine, went shopping.

Came back, started up machine, plugged in same USB stick ... "Not recognized"

I don't like not being able to use my stick, and I get very suspicious when things suddenly go wrong for no apparent reason! It's not the stick, because I've managed to access the files on it on another machine; so has something on my PC just decided to die?

Thanks in advance for advice and trouble-shooting!


Niels Grundtvig Nielsen
cook, musician, wordsmith, tram-lover ...
and, professionally speaking, author

```
*** with USB stick plugged in
[prompt]:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 7614:1237  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

*** no USB stick plugged in
[prompt]:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

---

### Post by runeh76 on 2010-12-01
> **engine said:**
> Ubuntu 10.04, Maxell 8Gb USB stick

First thing this morning, wrote a text file in Gedit, plugged in USB stick and saved file: no apparent problems.

Shut down machine, went shopping.

Came back, started up machine, plugged in same USB stick ... "Not recognized"

I don't like not being able to use my stick, and I get very suspicious when things suddenly go wrong for no apparent reason! It's not the stick, because I've managed to access the files on it on another machine; so has something on my PC just decided to die?

Thanks in advance for advice and trouble-shooting!


Niels Grundtvig Nielsen
cook, musician, wordsmith, tram-lover ...
and, professionally speaking, author

```
*** with USB stick plugged in
[prompt]:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 7614:1237  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

*** no USB stick plugged in
[prompt]:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```


I had same problems with my usb-sticks..playing around  :D
I learned one thing..if u get ur stick stuck like that, u need HP USB DISK storage format tool under win and format it fat32.. u can use virtualbox.

---

### Post by engine on 2010-12-05
Thanks for the tip! but it seems to be related to general flakiness now I've upgraded: sometimes the power off options don't appear top right, the USB isn't recognised and power off bottom right doesn't work &#8230; other times, everything is as it should be.

---

