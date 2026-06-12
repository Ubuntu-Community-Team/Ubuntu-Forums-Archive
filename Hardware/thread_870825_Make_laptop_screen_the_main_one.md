---
title: "Make laptop screen the main one?"
date: 2008-07-26
forum: Hardware
---

### Post by ngdias on 2008-07-26
I have a 13' Toshiba laptop and I'm trying to connect it to a 17' monitor.

I managed to make an extended screen adding in xorg.conf

```
       SubSection "Display"
           Depth		24
           Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
           # ADD A VIRTUAL LINE TO PROVIDE FOR THE LARGEST SCREENS YOU WILL HOTPLUG 
           Virtual              2048 2048 
       EndSubSection
```

and its working fine, BUT the 'main' screen with the top and bottom panels with the menus and applications is on the 17' monitor, not on the laptop screen.

I rather have it the other way around, as we get by default when configuring this setup in Windows or Mac. I searched online and played around with xrandr commands but I couldn't find a way to to this.

Help is appreciated.

---

### Post by ngdias on 2008-08-03
Nobody has a clue?

---

