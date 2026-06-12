---
title: "1920x1080 resolution gives grey screen"
date: 2013-09-12
forum: Hardware
---

### Post by sanderisraels on 2013-09-12
Can anyone help me with the following? I installed ubuntu 12.04 LTS. I could not select the native screen resolution of my monitor, which is 1920x1080. Ubuntu does recognize correctly that I have an Acer X243H monitor, but I cannot select a resolution higher than 1680x1050. I searched in the ubuntu forums and found a trick which allowed me to select 1920x1080 resolution. However it caused my monitor to become grey with some stripes in it. I have an ASUS H87M-E motherboard (which has an intel H87 express chipset) and I use it's build in graphics card. I tried searching for additional hardware drivers, but none were found. What do I need to do to get my monitor working at it's full resolution? Thanks in advance!!

---

### Post by Yellow Pasque on 2013-09-13
Using 12.04 on a system that new is like putting Windows XP on it. [http://www.phoronix.com/scan.php?page=news_item&px=MTM5MzU](http://www.phoronix.com/scan.php?page=news_item&px=MTM5MzU)

Get at least Ubuntu 13.04. I hesitate to recommend Ubuntu 13.10 because of the whole X/Mir thing, but Xubuntu 13.10 is a good option too.

---

### Post by CatKiller on 2013-09-14
12.04 is a perfectly valid option if you want Long Term Support.

It sounds like your trick was insufficient and your timings are off for that monitor.

---

### Post by Yellow Pasque on 2013-09-14
> 12.04 is a perfectly valid option if you want Long Term Support.
Disagree emphatically for Haswell..
The system will probably function, but 3D (and thus, Unity) is going to be dead slow without something like xorg-edgers PPA to give you mesa 9.2. And, in the OP's case, it looks like a recent kernel is needed to fix modesetting issues.

---

### Post by grentthevampire on 2013-09-14
```

[COLOR=#000000]cvt 1920 1080
[/COLOR]
```[COLOR=#000000]
now that will give you something like this
"[/COLOR]# 1920x1080 59.96 Hz (CVT 2.07M9) hsync: 67.16 kHz; pclk: 173.00 MHzModeline** "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -h**"
now copy that "**1920x1080......**" to your xrandr --newmode as parameter

```

xrandr --newmode "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync

```

check which device you want to output to:

```

xrandr -q

```

mine gives something like this
```

Screen 0: minimum 8 x 8, current 1366 x 768, maximum 16384 x 16384
DVI-I-0 disconnected (normal left inverted right x axis y axis)
VGA-0 connected 1366x768+0+0 (normal left inverted right x axis y axis) 410mm x 230mm
   1366x768       59.8*+
   1024x768       75.0     70.1     60.0  
   800x600        75.0     72.2     60.3     56.2  
   640x480        75.0     72.8     59.9  

```


if lets say you want to output 1980x1080 on VGA-0 you go something like this
```

xrandr --addmode VGA-0 "1920x1080_60.00"

```

now then proceed to 
```
xrandr --output VGA-0 --mode "1920x1080_60.00"

```

---

### Post by sanderisraels on 2013-10-17
Hi All, thanks for your answers and sorry for replying so late to them. I tried the solution posted by grentthevampire, this gave me the grey screen again. I also tried Ubuntu 13.10 just this evening, it did not make a difference. Then I installed ubuntu 13.04, so that I could install the intel graphics drivers (only available for 13.04), didn't help either...

---

### Post by sanderisraels on 2013-10-18
This morning I set the screen resolution to 1920x1080_60.00 again, got the grey screen again, but then I checked with the Menu button on my monitor which resolution was used. It gave 1920x1080 at 60 Hz. I've checked the manual of my monitor, and saw that my monitor can run 1920x1080 @ 60 Hz. When I had the grey screen, I started pressing some keys on my keyboard, I noticed that there were small changes on the screen, a horizontal bar changed color... If anybody has any ideas how to fix this issue, I'd be very happy!

---

