---
title: "Intel resolution"
date: 2007-06-14
forum: Hardware &amp; Laptops
---

### Post by readitsideways on 2007-06-14
Hi

I have an HP nx6110. Every thing is great - beryl too, but my resolution won't go over 1024x768

I've installed 915resolution which tells me the following:

Intel 800/900 Series VBIOS Hack : version 0.5.2

```
Chipset: 915GM
BIOS: TYPE 1
Mode Table Offset: $C0000 + $269
Mode Table Entries: 36

Mode 30 : 640x480, 8 bits/pixel
Mode 32 : 800x600, 8 bits/pixel
Mode 34 : 1024x768, 8 bits/pixel
Mode 38 : 1280x1024, 8 bits/pixel
Mode 3a : 1600x1200, 8 bits/pixel
Mode 3c : 1920x1440, 8 bits/pixel
Mode 41 : 640x480, 16 bits/pixel
Mode 43 : 800x600, 16 bits/pixel
Mode 45 : 1024x768, 16 bits/pixel
Mode 49 : 1280x1024, 16 bits/pixel
Mode 4b : 1600x1200, 16 bits/pixel
Mode 4d : 1920x1440, 16 bits/pixel
Mode 50 : 640x480, 32 bits/pixel
Mode 52 : 800x600, 32 bits/pixel
Mode 54 : 1024x768, 32 bits/pixel
Mode 58 : 1280x1024, 32 bits/pixel
Mode 5a : 1600x1200, 32 bits/pixel
Mode 5c : 1920x1440, 32 bits/pixel
```

My 915resolution file looks like so 

```
#
# 915resolution default
#
# find free modes by  /usr/sbin/915resolution -l
# and set it to MODE or set to 'MODE=auto'
#
# With 'auto' detection, the panel-size will be fetched from the VBE
# BIOS if possible and the highest-numbered mode in each bit-depth
# will be overwritten with the detected panel-size.
MODE=58
#
# and set resolutions for the mode.
# e.g. use XRESO=1024 and YRESO=768
XRESO=1280
YRESO=1024
#
# We can also set the pixel mode.
# e.g. use BIT=32
# Please note that this is optional,
# you can also leave this value blank.
BIT=32

```

when I run sudo 915resolution 58 1280 1024 nothing happens. I reboot and still no difference. The only option I have in settings>prefs>screen resolution is  1024x768.

Going through dpkg-reconfigure -phigh xserver-xorg and marking other resolutions and rebooting still only leaves me with  1024x768.

Any ideas? This is the one niggle left keeping my new Ubuntu experience from being perrrrfect

Thanks

Duncan

---

### Post by timbenton on 2007-06-14
I don't know what to tell you. On my Presario C300 all I had to do was install 915resolution from Synaptic and reboot. You shouldn't have to adjust anything. If you have some time what I'd do is reinstall Ubuntu and before you do anything else go into Synaptic and install 915resolution, then reboot immediately. Sometimes when you have changed settings or moved files things won't install correctly.

Only reinstall Ubuntu if you have free time and you can back up important documents, though.

---

### Post by readitsideways on 2007-06-18
It was my screen itself that can't handle a higher res...

---

