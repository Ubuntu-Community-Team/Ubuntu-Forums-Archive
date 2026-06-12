---
title: "Unity killed my resolution :("
date: 2011-05-01
forum: Hardware
---

### Post by Argentino on 2011-05-01
Hi Guys,

I upgraded to 11.04 today and now I get crap resolutions. I used to be able to get larger screen resolutions with 10.10. 

How can I force my old 1440X900 resolution?

Thank you!

---

### Post by ach667 on 2011-05-01
now dont take it from me as im having a major resolution problem but if this helps then so be it. I was messing with the terminal and found a command called xrandr it will force some changes on it. I think it goes like:
  ```
$ xrandr --output VGA1 --mode 1440X900 --rate 60
```

---

### Post by teachop on 2011-05-01
Continuing on that same line, perhaps run xrandr --verbose, and see if the mode exists first.

---

### Post by Argentino on 2011-05-03
Thanks guys,

I did:

```

$ cvt 1440 900
# 1440x900 59.89 Hz (CVT 1.30MA) hsync: 55.93 kHz; pclk: 106.50 MHz
Modeline "1440x900_60.00"  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync

$ xrandr --newmode name 106.50  1440 1528 1672 1904  900 903 909 934
xrandr: Failed to get size of gamma for output default

 $ xrandr --addmode default name
xrandr: Failed to get size of gamma for output default

```

But when I apply the new resolution mode on the "Monitors' applet, I get a notification that says:

"The selected configuration for displays could not be applied. Could not set the configuration for CRTC 262."

And no, the "xrandr --verbose" does not show the display I want, but before upgrading to 11.04, I was doing 1440X900 on 10.10. Makes me wonder what changed between the releases that confuses my video card :(

Any more help pleeeeeeease?

Thanks!

---

### Post by nomekop on 2011-05-05
the same exact thing happened to me. it wouldn't  let me pick my proper resolution 
this is what i did to fix it

**1**. when in ubuntu 11.04 click the power button in the upper right conner and and select **System Settings**. scroll down until you see **Additional Drivers **under **Hardware **and select it. you should see **NVIDIA accelerate graphics driver(version 173) **&[B] 
NVIDIA accelerated graphics driver(version current) [Recommended][/B].
 unactivated the ones that are activated. and go back and click the power button a select **restart to upgrade** (or something like that)

**2.** once it restarts login and it should be back to the normal resolution (fix it if not under **monitors**) and it should resemble ubuntu 10.10. go back to **Addditional Drivers **and activate[B] 
NVIDIA accelerated graphics driver(version current) [recommended][/B] then after that go to the power button and select **restart to upgrade**.

**3. **now go to **System Settings** and select **monitors **and your resolution should be there (if not keep reading)

**4.** if you completed all these steps above and still dont have your proper resolution then repeat step 1. once you login go to your terminal and tpye **sudo apt-get install unity** then press enter. after that tpye **sudo apt-get update unity** and press enter. now repeat steps 2 & 3. 

hope this works because it worked for me

---

