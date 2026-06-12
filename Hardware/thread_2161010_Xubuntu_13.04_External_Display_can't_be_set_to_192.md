---
title: "Xubuntu 13.04 External Display can't be set to 1920 × 1080"
date: 2013-07-09
forum: Hardware
---

### Post by rdp1976 on 2013-07-09
I just installed Xubuntu 13.04 with Windows 8 dual boot on my Dell XPS 13 (2013) Ultrabook.

All is good, except when I connect my ViewSonic HDMI 1080p Full HD External Monitor, it appears as Display DP1 in Xubuntu with a maximum screen resolution of 1024 x 768.

In Windows 8 I can set it to 1920 x 1080. Any suggestions?

Thanks in advance!

---

### Post by slickymaster on 2013-07-09
You can direct xrandr to set a different resolution. See this: [Resolution]("https://wiki.ubuntu.com/X/Config/Resolution/")

---

### Post by rdp1976 on 2013-07-10
No joy. When I try this:

xrandr --output DP1 --mode 1920x1080 --rate 60

I get the following:


xrandr: cannot find mode 1920x1080

Any other suggestions?

---

### Post by rdp1976 on 2013-07-10
After spending almost 3 hours playing around with xrandr, I've made some progress. The following commands "kind of" work:

[FONT=arial]xrandr --newmode "1920x1080_60.00" 148.50  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync[/FONT]
[FONT=arial]xrandr --addmode DP1 1920x1080[/FONT]
[FONT=arial]xrandr --output eDP1 --primary --mode 1920x1080 --output DP1 --mode 1920x1080 --left-of eDP1

Resolution on my external monitor looks "better", but is too wide and too tall - the standard date that appears in the top right hand corner is cut off in the middle of the day (eg, for Wednesday I can only see Wed before the edge of the screen). And this does NOT extend onto my laptop screen.

The newmode command is obviously incorrect. Any help in what it should be for a HDMI 1920x1080 monitor???

Pretty frustrating. Connecting my external display in Windows 8 took about 15 seconds. I've collectively spent over 4 hours on this simple problem so far.

Any help much appreciated....

[/FONT]

---

### Post by jp734 on 2013-07-11
Same thing happened with my Sony xbr before. I think I ended up with 1368x768 resolution, if I can remember it right. It was not 1920-1080 but the fonts and icons where acceptable.

---

### Post by slickymaster on 2013-07-11
> **rdp1976 said:**
> No joy. When I try this:

xrandr --output DP1 --mode 1920x1080 --rate 60

I get the following:


xrandr: cannot find mode 1920x1080

Any other suggestions?

Please see this [thread]("http://ubuntuforums.org/showthread.php?t=1364460&p=8560183&viewfull=1#post8560183").

---

### Post by rdp1976 on 2013-07-12
Thanks for the link to the other thread:
[http://ubuntuforums.org/showthread.php?t=1364460&p=8560183&viewfull=1#post8560183](http://ubuntuforums.org/showthread.php?t=1364460&p=8560183&viewfull=1#post8560183)

But unfortunately this didn't work either. I followed the instructions precisely, multiple times. The last command (STEP 4) below completely messes up my laptop display and my external display switches off completely.

I can't believe how difficult this is???? If I can't get my external monitor to work with Xubuntu, I basically can't use Xubuntu. Very frustrating........ wasted HOURS on this.

[FONT=arial]STEP 1
$ cvt 1920 1080
[/FONT]
[FONT=arial]
# 1920x1080 59.96 Hz (CVT 2.07M9) hsync: 67.16 kHz; pclk: 173.00 MHz
Modeline "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync

STEP 2
$ xrandr --newmode "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync[/FONT]
[FONT=arial]
STEP 3
$ xrandr --addmode DP1 1920x1080_60.00

STEP 4
$ xrandr --output DP1 --mode 1920x1080_60.00


Any help, please!

[/FONT]
[FONT=arial]:([/FONT]

---

### Post by rdp1976 on 2013-07-13
FYI, the monitor I am using is:

[COLOR=#000000][FONT=arial]ViewSonic VX2739WM[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]Model Number: VS12843[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]Optimum Resolution: 1920x1080 WUXGA

It is discontinued. [http://www.viewsonic.com/us/vx2739wm.html](http://www.viewsonic.com/us/vx2739wm.html)

Connecting to a new Dell XPS 13 (2013) ultrabook using the minidisplay port adapter:

[http://accessories.us.dell.com/sna/productdetail.aspx?c=us&l=en&s=dhs&cs=19&sku=331-2972](http://accessories.us.dell.com/sna/productdetail.aspx?c=us&l=en&s=dhs&cs=19&sku=331-2972)


[/FONT][/COLOR]

---

### Post by jp734 on 2013-07-13
Have you looked at xorg.0.log? Do you have xorg.conf file?

---

### Post by rdp1976 on 2013-07-13
There is no /etc/X11/xorg.conf file. Should I create one?

There is /var/log/Xorg.0.log. I'm not sure what I'm looking for in there. This is what it contains regarding DP1, the port my external display is connected to:

[    12.687] (II) intel(0): Printing probed modes for output DP1
[    12.687] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4
 kHz e)
[    12.687] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz
 e)
[    12.687] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz
 e)
[    12.687] (II) intel(0): Modeline "848x480"x60.0   33.75  848 864 976 1088  480 486 494 517 +hsync +vsync (31.0 kHz
 e)
[    12.687] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 489 492 525 -hsync -vsync (31.5 kHz 
e)

---

### Post by jp734 on 2013-07-13
Well not sure yet if you need to create one. Do you get the resolution you want if you boot the pc with the monitor hooked up?

---

### Post by rdp1976 on 2013-07-16
No. See earlier in the post. That's the whole problem.

I am connecting to the monitor via multidisplay port DP1 converter to VGA. In Windows 8, the external monitor appears perfectly as 1920 x 1080.

In Xubuntu, the max resolution is 1024 x 768. I can't work like that. I either get this external monitor working with 1920 x 1080 or I don't use Xubuntu.

Super frustrating...

---

### Post by jp734 on 2013-07-16
You've tried everything with xrandr so at this point, I don't see the harm on trying to create your own xorg.conf file. The thing with monitors is, its EDID should be automatically detected but for some reason, it just wont work on some monitors. That's when you need the xorg.conf file so you can specify its Horizontal and Vertical refresh rates:
 
I did some research on your monitor and this is what I've found, courtesy of [http://reviews.cnet.com/lcd-monitors/viewsonic-vx2739wm/4507-3174_7-34077676.html](http://reviews.cnet.com/lcd-monitors/viewsonic-vx2739wm/4507-3174_7-34077676.html)

It did not give me a range, just the max, but I think it should be safe with these numbers. [COLOR=#ff0000]**I'll leave that up to you.**[/COLOR]
[B][COLOR=#0000ff]
HorizSync 30.0-83.0
VertRefresh 50.0-76.0
[/COLOR][/B]
When you decide to create an xorg.conf file, make sure those are in your **[COLOR=#ff0000]Section "Monitor"[/COLOR]**. With a little bit of luck, your monitor should work on the 1920x1080 res.

**GOOD LUCK!**

---

### Post by rdp1976 on 2013-07-17
I don't know anything about xorg.conf files. I think I generated one (there wasn't one there) so what I have is a base template.

I have no idea how to add "my monitor" in there. The monitor section in the file looks like this (copied/pasted);

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Monitor Vendor"
    ModelName      "Monitor Model"
EndSection


Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Monitor Vendor"
    ModelName      "Monitor Model"
EndSection


Section "Monitor"
    Identifier     "Monitor2"
    VendorName     "Monitor Vendor"
    ModelName      "Monitor Model"
EndSection


Section "Monitor"
    Identifier     "Monitor3"
    VendorName     "Monitor Vendor"
    ModelName      "Monitor Model"
EndSection

---

### Post by jp734 on 2013-07-17
Those will work. Just add the refresh rates on one of them. You can change the identifier name to viewsonic to make it easier on you

---

### Post by rdp1976 on 2013-07-18
How do I know that the system is definitely USING the xorg.conf file?
I.e. if I make changes and nothing happens, how can I know for sure that it is at least referencing it?

---

### Post by jp734 on 2013-07-18
There are a lot of xorg.conf samples out there. Copy them and edit your monitor, device and screen sections making sure you enter the right driver for you card, the refresh rates for your monitor and the number of screen(s) for your layout.

Pay attention to all the identifiers on your configuration file. Make sure you give it a unique name and those names will be used and reported on your /var/log/Xorg.0.log. That's how you'll know if its being used.

---

### Post by rdp1976 on 2013-07-19
Yeah, the xorg.conf samples are pretty confusing. I tried to fill out the monitor section, but then Xubuntu wouldn't boot at all. I don't know. It seems to be a massive waste of time at this point. I've spent 3 weeks trying to figure out how to get a HDMI monitor to have 1920x1080 resolution. Windows figured it out in about 10 seconds. I don't know enough about xorg.conf files, so I'm just guessing...flying blind.

---

### Post by rdp1976 on 2013-07-19
Ok, I'm trying to stay positive about this. Given I've spent SO much time on it so far, I'm determined to get it working. But, man... Frustrated. I downloaded and xorg.conf example for Intel and swapped out the horizontal and vertical rates per your earlier message. This is it:

[FONT=arial]Section "Device"[/FONT]
[FONT=arial]  Identifier  "Device0"[/FONT]
[FONT=arial]  Driver      "intel"[/FONT]
[FONT=arial]  VendorName  "INTEL Corporation"[/FONT]
[FONT=arial]EndSection[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]Section "Screen"[/FONT]
[FONT=arial]  Identifier  "Screen0"[/FONT]
[FONT=arial]  Device      "Device0"[/FONT]
[FONT=arial]  Monitor     "HDMI2"[/FONT]
[FONT=arial]  DefaultDepth  24[/FONT]
[FONT=arial]  SubSection "Display"[/FONT]
[FONT=arial]    Depth       24[/FONT]
[FONT=arial]    Modes     "1920x1080@59.94p" "1920x1080@24p" "1920x1080@60p"[/FONT]
[FONT=arial]  EndSubSection[/FONT]
[FONT=arial]EndSection[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]Section "Monitor"[/FONT]
[FONT=arial]  Identifier  "HDMI2"[/FONT]
[FONT=arial]  HorizSync 30.0-83.0[/FONT]
[FONT=arial]  VertRefresh 50.0-76.0[/FONT]
[FONT=arial]  Option      "DPMS" "true"[/FONT]
[FONT=arial]  Modeline    "1920x1080@24p"     74.230 1920 2560 2604 2752 1080 1084 1089 1125 +hsync +vsync[/FONT]
[FONT=arial]  Modeline    "1920x1080@50p"    148.500 1920 2448 2492 2640 1080 1084 1089 1125 +hsync +vsync[/FONT]
[FONT=arial]  Modeline    "1920x1080@59.94p" 148.352 1920 1960 2016 2200 1080 1082 1088 1125 +hsync +vsync[/FONT]
[FONT=arial]  Modeline    "1920x1080@60p"    148.500 1920 2008 2056 2200 1080 1084 1089 1125 +hsync +vsync[/FONT]
[FONT=arial]EndSection[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]Section "Extensions"[/FONT]
[FONT=arial]  # fixes tearing[/FONT]
[FONT=arial]  Option      "Composite"           "Disable"[/FONT]
[FONT=arial]EndSection

I can see /var/log/Xorg.0.log is timestamped today, so it looks like the system is using the xorg.conf file. But nothing is changing. Same problem. No 1920x1080 resolution option in Display.

The log file isn't telling me anything intelligent to indicate (1) what is wrong and (2) how to fix it.......

Frustration continues!

[/FONT]

---

### Post by jp734 on 2013-07-20
What kernel are you using? Ive seen on some other posts where it worked fine  for them when they used kerner 3.7 but started having problem when upgraded to kernel 3.8 and higher. You might the same case

---

### Post by jp734 on 2013-07-20
I just checked xubuntu 13.04 uses kernel 3.8. I would try to download a live iso with kernel 3.7 and see if youll get the resolution.

---

### Post by robbie 348 on 2013-07-20
I had the same problem, it was using the default driver. I went to additional drivers, installed the first on the list and it solved it for me.

---

### Post by rdp1976 on 2013-07-20
I'm using Xubuntu 13.04. When I go to Settings Manager -> Software & Updates -> Additional Drivers it says "No proprietary drivers are in use" and there is no option to do anything (everything is grayed out).

---

### Post by rdp1976 on 2013-07-20
Kernel is:

# uname -r
3.8.0-26-generic

---

### Post by rdp1976 on 2013-07-20
Latest stable Linux Kernel on [https://www.kernel.org/](https://www.kernel.org/) is 3.10.1.

3.7 is not available. What are the commands to install a new version of the kernel?

---

### Post by rdp1976 on 2013-08-02
OK... Now that the forum is back after being hacked, are there any new insights into my problem?

I REALLY don't want to have to blast Xubuntu 13.04 away and install 12.04 JUST so that my external monitor can be set to 1920 x 1080.

Any help would be greatly appreciated :(

---

