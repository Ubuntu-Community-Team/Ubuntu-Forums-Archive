---
title: "display VGA undetected"
date: 2015-12-04
forum: Hardware
---

### Post by gianluca3 on 2015-12-04
hello,

I have a DELL XPS 13 with ubuntu 14.04.

During these two years I very often connected with HDMI projecters via the minidisplayport-HDMI connector without any problem. However, with VGA and corresponding connector I experienced always some troubles. Recently, the VGA display is undetected. When i run 
 
```
xrandr -q
Screen 0: minimum 320 x 200, current 1920 x 1080, maximum 32767 x 32767
eDP1 connected (normal left inverted right x axis y axis)
   1920x1080      60.0 +   59.9     48.0  
   1680x1050      60.0     59.9  
   1600x1024      60.2  
   1400x1050      60.0  
   1280x1024      60.0  
   1440x900       59.9  
   1280x960       60.0  
   1360x768       59.8     60.0  
   1152x864       60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
DP1 disconnected (normal left inverted right x axis y axis)
HDMI1 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 477mm x 268mm
   1920x1080      60.0*+
   1680x1050      59.9  
   1280x1024      60.0  
   1440x900       59.9  
   1280x800       59.9  
   1152x864       75.0  
   1280x720       60.0  
   1024x768       70.1     60.0  
   800x600        60.3     56.2  
   640x480        66.7     60.0  
   720x400        70.1  
VIRTUAL1 disconnected (normal left inverted right x axis y axis)
```

it seems that the VGA entry disappeared somehow.

Any hint or suggestion?

```

lspci
00:02.0 VGA compatible controller: Intel Corporation Haswell-ULT Integrated Graphics Controller (rev 0b)
```

---

### Post by mörgæs on 2015-12-06
For a Haswell graphics processor I don't think it makes sense to struggle with old software like 14.04. Phoronix has published a lot of articles on Haswell describing the gains of using an up to date Buntu, one of them is here:
[https://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-15.10-HSW-Gfx](https://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-15.10-HSW-Gfx)

I am aware that the VGA port is not mentioned but still I think it's worth a try to install 15.10.

---

### Post by gianluca3 on 2015-12-11
thanks for the reply, sorry for not having replied earlier, i missed somehow the notification.

i would like to avoid update for this minor issue unless it is clearly THE solution, which does not seem to be so

i look forward for alternative

best
g.

---

### Post by Yellow Pasque on 2015-12-11
There are different variants of the XPS 13, but I don't see any screenshots with the old school 15 pin D-Sub VGA port. All I see is Displayport outputs. Are you sure that your VGA port isn't a Displayport with a built-in DAC?

> i would like to avoid update for this minor issue unless it is clearly THE solution, which does not seem to be so
If it's not too much trouble (or bandwidth), you could always try a LiveUSB and see how that behaves.

---

### Post by gianluca3 on 2015-12-12
I'm connected with a minidisplay port-VGA adapter, with the HDMI I use the corresponding adapter as well.

The point is that "sometimes" it outputs the video on the screen even with the VGA but most of the time it just does not do anythink. I have tried different adapter, "sometimes" it worked just by switching adapter.

I know the description is weird...

I will try also with a liveUSB, thanks for the suggestion. 

thanks
g.

---

### Post by gianluca3 on 2016-05-18
An update to this, unsolved issue.

Meanwhile I have updated from 14.04 to 16.04 and, due to other reasons, changed the motherboard. The problem still is there.

I have tried to play around with xrandr following the many threads on that but with no success. I have added a mode and tried to force the output but nothing happened.

Maybe I have found a systematic issue. My laptop recognizes all the monitor and overhead projectors with VGA directly connected to the minidisplayport by an adapter but not the VGA that are "far" (long cables or after switches).

It is a very serious limitation for me and I do not have any idea on how to solve, any help is appreciated.

best
g.

---

### Post by him610 on 2016-05-18
You don't seem to be the only person with this problem. here is a discussion about same topic from 2009...
[https://arstechnica.com/civis//viewtopic.php?f=6&t=36570]("https://arstechnica.com/civis//viewtopic.php?f=6&t=36570")

Have you considered HDMI cable from your XPS13 to hdm-to-vga adapter connected to projector vga port?

---

### Post by gianluca3 on 2016-05-19
you mean two adapters then, minidisplayport-hdmi and then hdmi-vga.

i will try also this... 

thanks for the reply,
g.

---

### Post by gianluca3 on 2016-05-19
dear him610,

well, i borrowed one and it worked. so, with "long" VGA cable:

- minidisplay port-VGA  fails

- minidisplyaport-HDMI HDMI-VGA works

now i bought another adapter, i hope that there was not some magicians in the one that i borrowed and that this now solves (not elegantly) my problem... 

best
g.

---

