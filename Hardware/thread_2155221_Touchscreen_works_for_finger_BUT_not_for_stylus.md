---
title: "Touchscreen works for finger BUT not for stylus"
date: 2013-06-17
forum: Hardware
---

### Post by ppn029012 on 2013-06-17
Hi all,

I have problem to calibrate touchscreen for stylus.

When I use the finger, it always works very good. The stylus also works well before I did some system update(I am not sure what update is). 

After updated some package, the screen can sense the stylus but the cursor is super inaccurate, almost out of the screen. I can't calibrate it by system settings.

Here is some information,

[Ubuntu 13.04, Thinkpad X230t]

```

$ xinput list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Wacom ISDv4 E6 Pen stylus                   id=11    [slave  pointer  (2)]
&#9116;   &#8627; Wacom ISDv4 E6 Finger touch                 id=12    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                  id=14    [slave  pointer  (2)]
&#9116;   &#8627; Wacom ISDv4 E6 Pen eraser                   id=16    [slave  pointer  (2)]
&#9116;   &#8627; TPPS/2 IBM TrackPoint                       id=17    [slave  pointer  (2)]
&#9116;   &#8627; Logitech Unifying Device. Wireless PID:401b    id=9    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=8    [slave  keyboard (3)]
    &#8627; Integrated Camera                           id=10    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=13    [slave  keyboard (3)]
    &#8627; ThinkPad Extra Buttons                      id=15    [slave  keyboard (3)]

```

```
$ xinput list-props "Wacom ISDv4 E6 Pen stylus"
Device 'Wacom ISDv4 E6 Pen stylus':
  ...
    Wacom Tablet Area (289):    0, 0, 2776, 1569

```


```
$ xinput list-props "Wacom ISDv4 E6 Finger touch"
Device 'Wacom ISDv4 E6 Finger touch':
...
    Wacom Tablet Area (289):    930, 391, 5323, 8820



```
It seems that the cursor improves by changing the 'Wacom Tablet Area' property. But I can't figure out the accurate value for it?

How should I do?

Best

---

### Post by jimbobrob on 2013-06-19
Hey,   I had a similar if not the same issue with 13.04: the cursor of the stylus was out of the screen area and calibration made it even worse. I found a 'solution' in resetting the area for the stylus and the eraser. Not so elegant but efficient -- at least for me.    For the stylus:  ```
  xsetwacom --set "Wacom ISDv4 E6 Pen stylus" resetArea  
```    And for the eraser:    ```
  xsetwacom --set "Wacom ISDv4 E6 Pen eraser" resetArea 
```    Does this solution work for you?

---

### Post by Eraemaajaervi on 2013-06-20
thanks man!

had the same problem: the "Wacom Tablets & TabletPC Properties Tool" Calibration didn't do a good job, as well as the xinput_calibrator - both calibrations were off, not even close to being usable.

but once one of these were used, I couldn't figure out how to reset the whole thing, until i saw your post - thanks!

EDIT: If you know how to make this permanent, that would be nice. Whenever the screen is rotated I'm back to the old unusable settings.

EDIT 2: Found it. Use the dconf editor and go to ```
org.gnome.settings-daemon.peripherals.wacom
``` and change the area settings to whatever your output of ```
xsetwacom get "Wacom ISDv4 E6 Pen stylus" Area
``` is

do you also happen to know a fix for the edge-behavior? when going close to the left or the bottom edge with the stylus, the cursor moves slightly faster, which makes it hard to use the stylus precisely in these areas. the top and right edge this effect is almost not noticeable

---

### Post by ppn029012 on 2013-06-20
Yes! 
Thanks!!! It works pretty well.

What is the root of these problems??

Have you add these statements to your .bashrc?

---

### Post by jimbobrob on 2013-06-20
> **Eraemaajaervi said:**
>  had the same problem: the "Wacom Tablets & TabletPC Properties Tool" Calibration didn't do a good job, as well as the xinput_calibrator - both calibrations were off, not even close to being usable.   I guess both are the same; "Wacom Tablets & TabletPC Properties Tool" is just a GUI for xinput_calibrator. If I remember correctly, the GUI didn't even work for me under 12.04 at all.  > **Eraemaajaervi said:**
>  EDIT 2: Found it. Use the dconf editor and go to ```
org.gnome.settings-daemon.peripherals.wacom
``` and change the area settings to whatever your output of ```
xsetwacom get "Wacom ISDv4 E6 Pen stylus" Area
``` is  do you also happen to know a fix for the edge-behavior? when going close to the left or the bottom edge with the stylus, the cursor moves slightly faster, which makes it hard to use the stylus precisely in these areas. the top and right edge this effect is almost not noticeable  That's a nice solution. I just linked the rotation button with a very short script which handled the rotation and the resetting at once. Currently, I'm with OpenSuse but tonight I'm going to switch back to Ubuntu because of the fact I really like Unity... I will try your approach then!  Unfortunately, the edge behavior is not an OS based problem, it's a design problem of the screen (some kind of magnetic effect on the edges). There are a lot of threads all around the internet where people are complaining about this behavior. Well, I complained about this fact as well, but in every day use it doesn't bother me too much. It's just that the x230t is not the cheapest device out there and because of that it is a shame they were so sloppy in the manufacturing...   > **ppn029012 said:**
>  What is the root of these problems??  Have you add these statements to your .bashrc?  Actually, I don't know what the problem is. Maybe some driver issues?   Hm, I never used the .bashrc so far... what would be the use case?

---

