---
title: "X resolution woes"
date: 2005-06-14
forum: Hardware &amp; Laptops
---

### Post by gadge47 on 2005-06-14
I just installed Ubuntu onto a Dell Optiplex GX270 and I can't get X to display in anything other than 640x480.

The Dell has an integrated graphics chip: Intel 82865G
And the monitor I'm using is a Dell LCD: 1704FPV

I ran dpkg-reconfigure xserver-xorg and took most of the defaults except I tried disabling all modes except the "optimum" one for this LCD (1280x1024 @ 60Hz).

When I try to startx, it takes a while to come up and is in 640x480 mode. When I quit X I can see the following message that was printed to the console...

(1280x1024, DELL 1704FPV) mode clock 100000MHz exceeds DDC maximum 140MHz

This confuses me as I don't even see anything in xorg.conf that specifies the refresh rate.

I also tried changing the driver from "i810" to "vesa" but X wouldn't even start that way.

I tried looking on google but no one seems to be using this particular combo of hardware. Any help would be greately appreciated.

---

### Post by Xian on 2005-06-14
Best to try and eliminate the easy things first...

Open your xorg.conf file and post what is in the "Monitor" section.
```
$ sudo gedit /etc/X11/xorg.conf
```

---

### Post by gadge47 on 2005-06-14
Section "Monitor"
    Identifier "DELL 1704FPV"
    Option "DPMS"
EndSection

---

### Post by AMP on 2005-06-14
[QUOTE=gadge47]I just installed Ubuntu onto a Dell Optiplex GX270 and I can't get X to display in anything other than 640x480.

The Dell has an integrated graphics chip: Intel 82865G
And the monitor I'm using is a Dell LCD: 1704FPV

I ran dpkg-reconfigure xserver-xorg and took most of the defaults except I tried disabling all modes except the "optimum" one for this LCD (1280x1024 @ 60Hz).

When I try to startx, it takes a while to come up and is in 640x480 mode. When I quit X I can see the following message that was printed to the console...

(1280x1024, DELL 1704FPV) mode clock 100000MHz exceeds DDC maximum 140MHz

This confuses me as I don't even see anything in xorg.conf that specifies the refresh rate.

I also tried changing the driver from "i810" to "vesa" but X wouldn't even start that way.

I tried looking on google but no one seems to be using this particular combo of hardware. Any help would be greately appreciated.[/QUOTE]
 Okay login in a failsafe terminal and run

sudo dpkg-reconfigure xserver-xorg

then try and set it up that way, and reboot after each attempt to see if you did it right.

---

### Post by Xian on 2005-06-14
Okay, there is most likely your problem. You don't have any refresh and snyc rate parameters in that section. You'll need to break out or look up your monitor specs and find those settings, then add them into that section. While you're at it you might want to put in your display size if you can find that listed as well. You can calculate it by following this [How-To](http://www.advogato.org/person/robertc/diary.html?start=35) if it's not in the specs.

Here's my "Monitor" section.
You can use it as a guide (just plug in your own specs)

```
Section "Monitor"
        Identifier	"COMPAQ 7500"
        Option	"DPMS"
        HorizSync       30-70
        VertRefresh     50-140
        DisplaySize     312 234
EndSection
```

---

### Post by gadge47 on 2005-06-14
Thanks a bunch. That worked (I didn't set the screen dimensions but I did input the refresh rates that I found on Dell.com)


```
SectionMonitor
    Identifier "DELL 1704FPV"
    Option    "DPMS"
    HorizSync 30-81
    VertRefresh 56-76
EndSection
```

---

### Post by Xian on 2005-06-14
[QUOTE=gadge47]Thanks a bunch. That worked (I didn't set the screen dimensions but I did input the refresh rates that I found on Dell.com)
[/QUOTE]
Yeah, that's fine. If you don't notice any font issues on the GDM screen, or an offset space to the side of your monitor, then you probably have no need of that parameter.

---

### Post by vax on 2005-06-15
I have a similar problem:
when I installed ubuntu from LiveCD resolution is OK [1280x1024]
when installed on HD - max resolution is 1024x780

I tried to copy the Monitor lines from the LiveCD xorg.conf to the HD 's
but it doesnt work:it keeps with the low res.
 
is there anything else that I have to do rather than changing the configuration  file and restarting the computer?

---

### Post by wadesmart on 2005-06-17
06172005 1910 GMT-5

I just made the move to a all Ubuntu system. (Yea for me) However, I have had the display problems as well. Its at 640 x 480 and I cant see hardly anything. Even when certain windows open in Firefox I cant get to the side to close them.

I read the post by Xian and when I opened that file, I found just what gadge47 found. I read the article at [http://www.advogato.org/person/robertc/diary.html?start=35](http://www.advogato.org/person/robertc/diary.html?start=35) and Im just a bit unsure as to the edits to make. 

This is what Im thinking about putting:
SectionMonitor
    Identifier      "Envision EFT920"
    Option          "DPMS"
    HorizSync      30-98
    VertRefresh    50-160
    DisplaySize     Im stuck here.
EndSection

And these are my resolutions with refresh rates:
1600x1200@75Hz
640x350@70Hz
720x400@70Hz, 
640x480@60/72/75/85Hz, 
800x600@60/72/75/85Hz, 
1024x768@60/70/75/85Hz, 
1280x1024@60/75/85Hz, 
1600x1200@60/65/70/75Hz

Now when I ran xdpyinfo I got 640x480px = 361x271mm, Res 45x45 dots per inch. 
The page I referenced above said 1280x768 = 266x161mm.
So, do I put the display size for one, more than one, just the ones I want, ???

1280x768px = 266x161mm = 4.812 and 4.77  (1280/266=4.812)

If I wants, lets say 1280x1024 that would by 266x212(approx). 

Is what what I put 266-212?
Wade

---

### Post by wadesmart on 2005-06-17
Oh, one more thing, 

Dot pitch is .21mm x .25mm and the preset display is 346mm x 260mm (640x480?)

Wade

---

### Post by wadesmart on 2005-06-17
06172005 2052 GMT-5

I got it to work! I have a screen that I can work on now. 

Wade

---

### Post by jbandsma on 2005-06-19
[QUOTE=Xian]Best to try and eliminate the easy things first...

Open your xorg.conf file and post what is in the "Monitor" section.
```
$ sudo gedit /etc/X11/xorg.conf
```[/QUOTE]


Monitor
Identifier  "compaq 7550
Option       "DPMS"

However, gedit only opens the file in read-only mode and I can't figure out how to change that in order to do the necessary edits.

---

### Post by estel on 2005-06-19
Go into the Terminal (Applications -> System Tools -> Terminal).
Type 
```
sudo gedit /etc/X11/xorg.conf
```
Then type the root password (yours).
This will open gedit so that you can write it. Another way is to (Applications -> System Tools -> Run as a different user) Run gedit as root.

---

### Post by jbandsma on 2005-06-19
It won't accept my password for root functions. I've already tried that. I was never asked to set any passwords except the one for my user name.

---

### Post by jbandsma on 2005-06-20
[QUOTE=estel]Go into the Terminal (Applications -> System Tools -> Terminal).
Type 
```
sudo gedit /etc/X11/xorg.conf
```
Then type the root password (yours).
This will open gedit so that you can write it. Another way is to (Applications -> System Tools -> Run as a different user) Run gedit as root.[/QUOTE]


I finally got it changed. Thanks to everyone who put up with what had to be the 7000th time this question has been solved before.

 \\:D/

---

