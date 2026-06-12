---
title: "Newbie needs help with Screen resolutions"
date: 2010-02-26
forum: Hardware
---

### Post by kinton on 2010-02-26
Hi guys, after being an avid windows fan for many years I decided to go for a change and install Ubuntu 9.10 on a pc i recently built. I love the OS, but am completely baffled by the screen resolution issue.

After reading forum post for hours on end I was getting no where, so i decided to make my own post. I'm sorry because i'm aware there are fixes and guides out there already but I simply dont understand how to follow them.

Basically I want to set my screen resolution to 1680 x 1050. Thats all.

I am a complete beginner to Ubuntu so please speak slowly! :)
Thanks,
Matt

---

### Post by efflandt on 2010-02-26
If your screen was digitally connected (DVI or HDMI) X should automatically recognize its native resolution.  But VGA can be more temperamental and/or this is the first I ever heard of that resolution.  Look through /var/log/Xorg.0.log to see what video modes X recognizes for it.  It may not activate some video modes that may actually work.

You do not say what video card/chip you have or whether you are using standard modules, but generally see [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

Although, **cvt** does not always come up with a modeline with optimum timings.  The mode it came up with for a 1080p HDTV was vertically correct, but horizontally scrunched and offset.  But I got a mode from /var/log/Xorg.0.log of a DVI to HDMI connected desktop that worked properly for my VGA connected laptop.

---

### Post by kinton on 2010-02-27
Thanks for the reply, my video card is a Radeon HD 4350. I was originally connecting to a dell monitor via VGA, however when I installed the driver for my video card onto Ubuntu, it will no longer work because the default setting is too high and I cannot change it because when I start up the computer a black screen is displayed.

I have therefore connected it to my HDTV, this works however I do not want to keep it on there as it is a family PC.
 
I have looked at that link, followed the instructions but it still doesnt work.
 
Thanks

---

### Post by kinton on 2010-02-27
Ok, I have uninstalled the video card driver so i am currently running on my VGA monitor at 1152x864. 

I have followed the instructions on creating modelines, but when I try and add a new modeline I get the following error: 

X Error of failed request:  BadName (named color or font does not exist)
  Major opcode of failed request:  150 (RANDR)
  Minor opcode of failed request:  16 (RRCreateMode)
  Serial number of failed request:  25
  Current serial number in output stream:  25

---

### Post by efflandt on 2010-02-27
Yes VGA tends to default to 1152x864 for monitors capable of more than that.

What is the output of just plain **xrandr**?  That should list the name to use for xrandr (VGA-0?) when assigning a mode to an output or switching to it.

Not sure what you get when you do **cvt 1680 1050**, but I get:

# 1680x1050 59.95 Hz (CVT 1.76MA) hsync: 65.29 kHz; pclk: 146.25 MHz
Modeline [COLOR=Red]"1680x1050_60.00"  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync[/COLOR]

Or gtf 1680 1050 60 comes up with:

  # 1680x1050 @ 60.00 Hz (GTF) hsync: 65.22 kHz; pclk: 147.14 MHz
  Modeline [COLOR=Red]"1680x1050_60.00"  147.14  1680 1784 1968 2256  1050 1051 1054 1087  -HSync +Vsync[/COLOR]


So assuming your device is VGA-0 (or use whatever xrandr shows it is) you could copy the part I marked in red from one of those and try pasting that as a newmode (don't miss the +vsync on the end):

```
xrandr --newmode "1680x1050_60.00"  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync
xrandr --addmode VGA-0 1680x1050_60.00
xrandr --output VGA-0 --mode 1680x1050_60.00
```I cannot guaranty if that will work, but it is a starting point.

---

### Post by kinton on 2010-03-01
Hi, the method works perfectly!

However, everytime I shut down the PC it goes back to the old resolution, how can I keep my new one?

EDIT: I tried to follow this guide [http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html](http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html) and I can change the file, but cannot save it because it is Read Only. Any ideas on how to change this?

Thanks
Matt

---

