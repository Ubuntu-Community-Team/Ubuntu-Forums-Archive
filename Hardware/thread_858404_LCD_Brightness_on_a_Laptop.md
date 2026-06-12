---
title: "LCD Brightness on a Laptop"
date: 2008-07-13
forum: Hardware
---

### Post by SyntheticShield on 2008-07-13
My LCD brightness on my laptop seems dim.  When I boot to windows its not like that.  Is there some type of driver or something I can download for to help with this.

This is on my Averatec 7100 series laptop with a 17" screen using an AMD 3100+ Sempron processor.

---

### Post by sdennie on 2008-07-13
Try looking in System->Preferences->Power Management.  If you can't adjust the backlight brightness there, see if xbacklight works for you:

```

sudo apt-get install xbacklight

```

Then, for instance, to set the backlight at 50%, try:

```

xbacklight -set 50

```

---

