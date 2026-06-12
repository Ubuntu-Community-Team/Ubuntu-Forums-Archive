---
title: "Help on HP laptop devices"
date: 2012-10-01
forum: Hardware
---

### Post by mths95 on 2012-10-01
I have a 2011 Pavilon dv5 2115 (Brazilian variant) which never worked well running any OS but Windows 7. I have tried Ubuntu and Debian before but because the lack of support for some hardware, I always return to Windows.

Recently, I feel the need for a Linux distro and decided to give a chance to 12.04. All went well except for the issues I am going to list and claim help:


[LIST]
[*]The laptop goes extremely hot, fan makes such a noise
[*][COLOR=Silver]The touchpad is a infamous Synaptics Clickpad which is relatively easy to activate right click, but it doesn't work like on Windows 7, with some habitual gestures (scrolling) and click and drag support[/COLOR]
[*]The bluetooth (rt3090 card) needs to be reseted with "bccmd psset -r -s 0x0000 0x028c 0x0001" always I need using it
[*]VLC and others players are using GPU acceleration, but the videos pixelate sometimes and are unplayble using only battery. I have tried "fglrx" and "fglrx-updates" packages and they behave the same. I stick with "-updates" and HDMI is working well.
[/LIST]
Sorry my bad English, but all I want is stable *nix platform to use. I gave up of using Windows for my needs.


Oh, the specifications of interest:



[LIST]
[*]AMD Turion II P520
[*]AMD/ATI Mobile HD4250
[*]RT3090 (cheap and poor WiFi/Bluetooth card)
[*][COLOR=Silver]Synaptics Clickpad[/COLOR]
[/LIST]

---

### Post by mths95 on 2012-10-02
anyone?

---

