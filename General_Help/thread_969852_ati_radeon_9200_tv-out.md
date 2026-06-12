---
title: "ati radeon 9200 tv-out??"
date: 2008-11-03
forum: General Help
---

### Post by nimsu on 2008-11-03
i have a radeon 9200 and am trying to get the tv-out portion to work properly. I;ve tried a bunch of different guides and the best I could do was 800 x600, but it looked like a mess. I want to shoot for 1024 x768 (or something decent) so I can watch full screen movies. any advice would be appreciated


__________
so now the monitor and tv show output as my computer loads. the tv even show the ubuntu graphic. but once startx loads the tv blanks out

---

### Post by nimsu on 2008-11-04
bump

---

### Post by Xsoldier2000 on 2008-11-05
me too, me too. Exact same problem here. 


...well that and my USB Creative Live isn't working...but one problem at a time, right?

---

### Post by rubberglove on 2008-11-05
I have a radeon 9200 and managed to get the tv-out working at some point over the past year. This may not be the sexiest way of doing it, but it works well for me. It's been a while since I had to think about it, but I remember it was not the easiest thing to figure out.

One thing first, though, is that the tv-output is 800x600 (you are talking about the rca/s-video output, right?)

First, you need a line in your xorg.conf like this:

virtual xxxx yyyy

Where xxxx and yyyy are the width and height of a 'virtual screen' that is big enough to contain your monitor's resolution size plus the 800x600 tv-output.  

That is, if your monitor is 1024x768 you would have

```
virtual 1824 768
```

since 1024 + 800 = 1824.
    ______
____|*****|
|800|1024 |
|___|_____|

(tv-output 'beside' monitor)

my main monitor is 1680x1050, so I should do 

```
virtual 2480 1050
```

However (complication!), there's a problem with that if you are using compiz (desktop effects). The card is only able to do 3d acceleration on a virtual screen size of 2048x2048 (or something like that). SO, I do 

```
virtual 1680 1650
```

where 1650 is 1050+600
____
|800|
|___|__
|*****|
|1680 |
|_____|

(tv-output 'above' monitor. yay ascii art!).

Here's what I have for my xorg.conf

```
Section "Device"
    Identifier  "Configured Video Device"
EndSection

Section "Monitor"
    Identifier  "Configured Monitor"
EndSection

Section "Screen"
    Identifier  "Default Screen"
    Monitor     "Configured Monitor"
    Device      "Configured Video Device"
    SubSection "Display"
        Virtual 1680 1650
        Modes       "1680x1050" "1440x900" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection
```

that's for intrepid -- for earlier versions (hardy, etc) there will be a lot more in there, but you should just be able to add the 'virtual' line in the Display section.

once that's done (and you've rebooted or restarted X)
You should be able to run:

```
xrandr --addmode S-video 800x600
xrandr --output S-video --mode 800x600 --rate 60 --above DVI-0
```

in the terminal to turn on the tv-output (if you want your tv-output to be beside your monitor, replace '--above' with '--left-of or --right-of') In my case, having the tv-output 'above' my monitor is a little awkward, having to drag windows to the top-left of the screen to get them to appear on the tv, but I've gotten used to it (the physical tv is across the room anyway). 

Since some applications will behave a bit 'funny' when you change the size of the desktop on them (dropdowns and menus in firefox and thunderbird) and because I don't like windows and popups getting placed onto my tv screen, I turn the tv-output off when I'm not using it:

```
xrandr --output S-video --off
```


I actually put this into a (poorly written) script called tv-out.sh and assigned it to some hotkeys:

```
#!/bin/bash
if [ -n "$1" ]
then
xrandr --addmode S-video 800x600
xrandr --output S-video --mode 800x600 --rate 60 --above DVI-0
else
xrandr --output S-video --off
echo "done"
fi

```

so running 

```
tv-out.sh on
``` will turn it on and ```
tv-out.sh
``` will turn it off. 

Let me know if any of that makes sense.
If you need some clarification or more help, make sure to include:

- which version of ubuntu you are running
- a copy of your xorg.conf


cheers!

---

