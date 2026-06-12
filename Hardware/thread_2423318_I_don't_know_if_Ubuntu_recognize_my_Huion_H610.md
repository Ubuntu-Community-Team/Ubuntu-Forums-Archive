---
title: "I don't know if Ubuntu recognize my Huion H610?"
date: 2019-07-20
forum: Hardware
---

### Post by min-liban on 2019-07-20
I recently came from Windows and I'm having a bit of a problem trying to set in with my drawing tablet. First, Krita crashed as soon as moved the pen in a recent open file making me inable to use it, but gladly it was fixed with just a software upgrade. Now, I'm left hand and I want to invert the tablet's axis but when I go to configurations and enable it nothing happens.
When I try to use ```
xsetwacom --list devices
``` it inputs nothing (expected) but when I try ```
lsusb
``` it prints this:
```
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 04f2:b573 Chicony Electronics Co., Ltd 
Bus 001 Device 004: ID 04ca:3014 Lite-On Technology Corp. 
Bus 001 Device 005: ID 0101:0007  
Bus 001 Device 007: ID 256c:006e  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```
I come to the conclusion that the entry 7 is my tablet but it's kinda weird? It has no name. I don't know what to do all I want is to use it in left hand mode.

edit: also, I tried this tutorial in the past, but it completely crashed my system. It wasnt even recognizing my mouse or touchpad
[https://askubuntu.com/questions/500141/huion-h610-tablet](https://askubuntu.com/questions/500141/huion-h610-tablet)

---

