---
title: "xrandr or 915resolution to get 1280x1024 on extern TFT"
date: 2007-07-28
forum: Hardware &amp; Laptops
---

### Post by mwerlberger on 2007-07-28
Hi!

Just played around with different variants of settings but i don't get the resolution of my Samsung Q35 to 1280x1024 on a extern TFT (Eizo S1910) connected via VGA. Im using Feisty and using xrand i have the problem that 1280x800 is the best thing it can do.

```

mwerlberger@tweety:~$ xrandr  -q
 SZ:    Pixels          Physical       Refresh
*0   1280 x 800    ( 382mm x 303mm )  *60  
 1   1024 x 768    ( 382mm x 303mm )   75  
 2    800 x 600    ( 382mm x 303mm )   75  
 3    640 x 480    ( 382mm x 303mm )   75  
Current rotation - normal
Current reflection - none
Rotations possible - normal left inverted right 
Reflections possible - none

```

After some googling and searching in forums and the xorg mailing list i came across the script 915resolution. Installed it via apt and there it can do 1280x1024?!

```

mwerlberger@tweety:~$ sudo 915resolution -l
Intel 800/900 Series VBIOS Hack : version 0.5.2

Chipset: 945GM
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
Mode 60 : 1280x800, 8 bits/pixel
Mode 61 : 1280x800, 16 bits/pixel
Mode 62 : 1280x800, 32 bits/pixel

```

But doing a 'sudo 915resolution 49 1280 1024 16' does not change anything. Am i missing something or do i have to use it a different way?

Maybe somebody can help me with that issue.

Ah yes....: I'm using E17 as desktop manager but still the gnome-settings-deamon is running to get cute fonts for gtk things and such stuff. Could there be a problem? Changing the resolution in e17 or gnome-display-properties are not possible either. The best that can be selected is 1280x800 and i would really like to work on the extern tft at home with 1280x1024..... (no xinerama or stuff like this... only the extern one alone...).

Hope somebody have some gut tips for me.

Rgds,
 Manuel

---

### Post by mwerlberger on 2007-07-30
no ideas? no hints?
Nobody having similar problems?

Would be really happy about something... anything....

Rgds,
 Manuel

---

