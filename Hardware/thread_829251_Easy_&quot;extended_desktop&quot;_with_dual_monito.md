---
title: "Easy &quot;extended desktop&quot; with dual monitors"
date: 2008-06-14
forum: Hardware
---

### Post by Simon Shine on 2008-06-14
Hi there

As I recently succeeded in having my Lenovo x41 laptop 12" and an external 22" widescreen monitor display a split screen, or what Windows calls an "extended desktop" (moving cursor to the edge, it pops over to the next screen), I thought I'd share my success. My laptop has an Intel  Mobile 915GM graphics card, and having heard bad things about intel and graphics drivers, it was still very easy, but it took some figuring out.

To start with, plugging in my second monitor made X11 set the display to 1680x1050 (my 22" widescreen default) and my laptop's monitor to only a portion of the full X11 display (1024x768). This doesn't work the way I like it because the small monitor is completely redundant. For this I use a tool called "xrandr" (or its graphical interface "grandr" which you need to install using apt-get first). I could also use Systems -> Preferences -> Screen Resolution, but this didn't work at first for me.

grandr names my screens "LVDS" for my laptop monitor and "VGA" for my external monitor. Going into the "Layout" section of the program I can set the relative position of the screen display. I initially got an error saying that the user view area was exceeded, and I fixed this with a small addition to my /etc/X11/xorg.conf:

```
Section "Screen"
    Identifier  "Default Screen"
    Device      "Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
    Monitor     "Generic Monitor"
    DefaultDepth    24
[B]    SubSection "Display"
        Virtual 2704 1050
    EndSubSection[/B]
EndSection

```

The trick here was to figure out what my total "virtual" screen resolution was going to be: one plus the other, meaning the width would be 1680 + 1024 = 2704, and the height would just be 1050 (since the small portion does not exceed the large when they are left and right to each other).

Note that I didn't have to add another "Screen" or "Monitor" section as I have read in most guides.

Restarting X11 didn't yield good results at first, but adjusting the screen portions again in grandr gave me what I wanted! Doing a screenshot I get a huge image with both portions of the screen in it, just like in Windows.

Now my only grudge is that I can actually move my cursor into the part of the 2704x1050 square that isn't covered by a screen, illustrated by the blank spaces in the ascii art below.

```

1111111112222222222222222222222
1111111112222222222222222222222
1111111112222222222222222222222
1111111112222222222222222222222
         2222222222222222222222
         2222222222222222222222

```

A fix for this would be appreciated, but otherwise it's to live with.

---

### Post by ljungkvist on 2008-06-14
what a coincidence, actually i just did almost the exact thing.

i have a Compaq Presario V6000 laptop (Celeron processor, 945 graphics), on which i pretty recently installed hardy. Most things worked well, but the things that weren't really satisfactory were the wireless and the multiple displays. the wireless has been partly solved through [this guide]("http://ubuntuforums.org/showthread.php?t=769990&highlight=presario") (just some minor flaws at the moment).

Concerning the other issue, what i wanted to do was to connect a 19' tft to the vga-out and extend the desktop onto it. The first thing I found after searchning the ubuntu forum was a lot of how-to's applying a xorg.conf-modifying approach. This all was very complicated and after a good day i was almost about to give. that was when i found [this site]("http://wiki.debian.org/XStrikeForce/HowToRandR12"), which solved my problem in like one minute. Of course this is the same method you used.

And just as you my only concern is the fact that the "no-mans-land" which isn't covered by any display is availiable to mouse movements. So +1 on your request for a fix of this.

---

