---
title: "How to change RGB levels without installing third-party software?"
date: 2022-03-31
forum: Hardware
---

### Post by username2758 on 2022-03-31
Hello,

I have this Acer Aspire 5 laptop which has an IPS panel that is badly calibrated out of the box, it looks kind of blueish.

So my question is it possible to change RGB levels without installing any third-party software on Ubuntu?

I am using Ubuntu 20.04.4 LTS with Wayland on this laptop:```
$ sudo inxi -G
Graphics:
  Device-1: AMD driver: amdgpu v: kernel 
  Display: server: X.Org 1.20.13 driver: amdgpu resolution: 1920x1080~60Hz 
  OpenGL: renderer: AMD RENOIR (DRM 3.41.0 5.13.0-30-generic LLVM 12.0.0) 
  v: 4.6 Mesa 21.2.6
```

---

### Post by him610 on 2022-03-31
I use xgamma to darken my screen from an overly bright presentation. Maybe you could experiment with it to see if it might suit your purposes. Run it from a terminal.
```

 xgamma -gamma 0.8

```

---

### Post by username2758 on 2022-03-31
Thanks! But isn't there sort of a config file in which I can change gamma, brightness, red, green and blue levels individually?

---

### Post by him610 on 2022-03-31
```
 man xgamma
```
There is a section in the man page that explains how to set individual R, G, B components
```
....
       -gamma f.f
               The  gamma  correction  can either be defined as a single value, or separately
               for the red, green and blue components. This argument specifies the gamma cor&#8208;
               rection as a single value.

       -rgamma f.f
               This argument specifies the red component of the gamma correction.

       -ggamma f.f
               This argument specifies the green component of the gamma correction.

       -bgamma f.f
               This argument specifies the blue component of the gamma correction.

```
You need to figure it out for yourself.

---

### Post by username2758 on 2022-04-01
Thanks again but it isn't working. The values are not being applied but not sure why.```
ubuntu64@a515-45:~$ xgamma -rgamma 0.7 -bgamma 0.3 -ggamma 0.5
-> Red  1.000, Green  1.000, Blue  1.000
<- Red  1.000, Green  1.000, Blue  1.000
ubuntu64@a515-45:~$ xgamma -rgamma 0.7 -bgamma 0.3 -ggamma 0.5
-> Red  1.000, Green  1.000, Blue  1.000
<- Red  1.000, Green  1.000, Blue  1.000
```

---

### Post by him610 on 2022-04-02
As I suggested earlier, you need to figure it out....(this one tints every thing green)
```
xgamma -rgamma 1. -bgamma 0.8 -ggamma 1.2
```
Consider: the default gamma setting is 1.0. Change each individual RGB value in smaller increments to effect any change. Eventually, you may find a color combo that suits you.

---

### Post by Holger_Gehrke on 2022-04-02
Alternatively there's a '--gamma' option to xrandr since xgamma's man-page warns that xgamma should be considered obsolete.
```

xrandr --output HDMI-0 --gamma 0.9:1:1

```
reduces red slightly on my external display connected through the HDMI port of my laptop. You can find out the name(s) for the --output option - which is necessary for the gamma option to be recognized - with 'xrandr' without any options or parameters.

Holger

---

### Post by him610 on 2022-04-02
@Hoger_Gehrke

Thanks, I just updated my script.
```

xrandr --output HDMI-0 --gamma 0.8:0.8:0.8

```
Darkens the screen just like it did before.

---

### Post by Holger_Gehrke on 2022-04-02
And returning to the original question: I completely overlooked that you say you're using Wayland. As far as I can tell, if there's no settings in the graphical tools you're out of luck because Wayland tends towards graphical tools first, command line only if forced at gunpoint. I found some talk about adding support for colour management / colour calibration going back to 2020 and some mention of developer builds having some kind of functionality in this area at the end of 2021 but no announcement that it was done and available for users.

Holger

---

