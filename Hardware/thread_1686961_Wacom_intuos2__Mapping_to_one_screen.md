---
title: "Wacom intuos2 / Mapping to one screen"
date: 2011-02-13
forum: Hardware
---

### Post by Pyoo on 2011-02-13
Hi dear community !
I would like to start by saying 2 things :
*I am a very new beginner on Linux and Ubuntu. I have installed it 6 hours ago and i am discovering everything at once. I am an illustrator, not a programer, but i have some little experience and some kind of common sense (I hope) :p
*I have looked for a solution to this problem in different places, but as I am a very beginner it is really too blurry for my level and i do not know where to start.
i have been visiting for example :
[http://ubuntuforums.org/showthread.php?t=1350123](http://ubuntuforums.org/showthread.php?t=1350123)
[https://help.ubuntu.com/community/Wacom.fdi](https://help.ubuntu.com/community/Wacom.fdi)
and the wacom page of sourceforge

So here is an overview of my situation :
1-New installation of Ubuntu 10.10, 64 bits, gnome
2-An intuos 2 A4 "Oversize" graphic tablet 12x12 
3-Two screens on dualview mode, plugged on a nvidia 8800gt :
the left one (main) in 1920x1080, the right one in 1680x1050

_Problem :_ When I use the pen on my tablet to draw a circle, it makes an ellipse on the screen
_Diagnosis : _the tablet is not well mapped. The tablet should be adapted to the ratio of my main screen. I suppose that if I use 100% of the width and height of my main screen, i will have to use 100% of the width of my tablet + a certain %age of its height.

I hope someone will help me, I really don't know where to look after having read all this stuff. I have no global view on linux, I have just jumped out of the windows matrix, hoping i could be an illustrator only using linux, but it seems it may be more difficult than expected :p

thanks by advance,
yoann

---

### Post by Pyoo on 2011-02-13
I have made some great steps on my way. Well steps that would appear tiny for you maybe :p.
I managed to install the xf86-input-wacom build system, and then i did a : "xinput list"
i get :
&#9116;   &#8627; Wacom Intuos2 12x12 eraser                  id=11    [slave  pointer  (2)]
&#9116;   &#8627; Wacom Intuos2 12x12 cursor                  id=12    [slave  pointer  (2)]
&#9116;   &#8627; Wacom Intuos2 12x12 stylus                  id=13    [slave  pointer  (2)]

When I try then a : xinput list-props "Wacom Intuos2 12x12 stylus"
I get :
Device 'Wacom Intuos2 12x12 stylus':
    Device Enabled (121):    1
    Coordinate Transformation Matrix (123):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
    Device Accel Profile (248):    0
    Device Accel Constant Deceleration (249):    1.000000
    Device Accel Adaptive Deceleration (250):    1.000000
    Device Accel Velocity Scaling (251):    10.000000
    Wacom Tablet Area (283):    0, 0, 30480, 31680
    Wacom Rotation (284):    0
    Wacom Pressurecurve (285):    0, 0, 100, 100
    Wacom Serial IDs (286):    68, 0, 2, 0
    Wacom TwinView Resolution (287):    0, 0, 0, 0
    Wacom Display Options (288):    -1, 0, 1
    Wacom Screen Area (289):    0, 0, 3600, 1080
    Wacom Proximity Threshold (290):    10
    Wacom Capacity (291):    -1
    Wacom Pressure Threshold (292):    27
    Wacom Sample and Suppress (293):    2, 4
    Wacom Enable Touch (294):    0
    Wacom Hover Click (295):    1
    Wacom Enable Touch Gesture (296):    0
    Wacom Touch Gesture Parameters (297):    50, 20, 250
    Wacom Tool Type (298):    "STYLUS" (300)
    Wacom Button Actions (299):    "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0)

I think i am on the good way ...

---

### Post by Pyoo on 2011-02-13
I have finally solved my problem !
In the end, it is not exactly doing what i wanting at the beginning, it does better :p.
I can now go from one screen to the other, and i have no deformation of drawing. Though, i loose a part of the active surface of the tablet down, but it is not really a problem =).

To try to sum up the way i suceeded is a bit complicated because i have done a loooot of things. Remember i was knowing nothing about linux and code before this morning........

But i could say :
1- have to be sure to have the xf86-input-wacom.
2- have to be sure to have the good packages and depencies
3- you have to find the good coordinate transformation matrix coefficient. It can be mind tricky if you are not keen on maths like i do :p

Yoann

---

### Post by Favux on 2011-02-13
Hi Yoann,

Welcome to Ubuntu forums!

Nice job!  It sounds like you have everything working from a standing start in a short time.

If you're interested in developing a xsetwacom script for your Intuos 2 A4 "Oversize" graphic tablet 12x12 let me know.

Also would you mind sharing/posting your monitor specific transformations for your monitors; the left one (main) 1920x1080, the right one 1680x1050?

---

### Post by Pyoo on 2011-02-13
Hi Favux !
I have actually found the way to create my command line and launch it at every startup, but thanks !

there are 2 needed in fact, one for each detected device :
xinput set-prop "Wacom Intuos2 12x12 stylus" --type=float "Coordinate Transformation Matrix" 1 0 0 0 2.5 0 0 0 1
xinput set-prop "Wacom Intuos2 12x12 eraser" --type=float "Coordinate Transformation Matrix" 1 0 0 0 2.5 0 0 0 1

As you see, the parameter 2.5 was working to be able to work with the pen on my 2 screens + having no deformation when drawing.
This page was helping a lot on the way : [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Dual_and_Multi-Monitor_Set_Up](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Dual_and_Multi-Monitor_Set_Up)

_2 things to know though :_
*This 2.5 factor was found a bit by experimenting ^^. I guess it is possible to find something more accurate than I did. At least I don't feel for now any problem when drawing.
*You have to know that a portion of the down part of my tablet is of no use now because of the mapping. It is not really a problem i have to say.

I am honnestly very proud to have fixed this problem today, since it was my first day on linux and i am just an artist, not a programer :p. I have been through a lot of documentation and websites to understand the issues, and i have to thank again the community for that has been done.

I am confident that i will manage to completely become independant from windows in my 2d/3d illustration future job, even though i know there will have some very tough things to make work.

Bye !
Yoann

---

### Post by Favux on 2011-02-13
Great!  Thanks for sharing what you did.  That's the idea of the forum.  And you should be proud.  That's a lot to learn and accomplish in such a short time!

I'm glad you found the Dual and Multi-Monitor page on the LWP mediawiki helpful.  That's one of "my" pages, although Peter did the MaptoOutput section and I just edited it a little.  It basically duplicates the [HOW TO Setup a Wacom Tablet with Multi-Monitors in Maverick and Natty]("http://ubuntuforums.org/showthread.php?t=1656089") on this forum.

I was thinking of an xsetwacom startup script for your stylus and eraser and buttons/pad.  Samples are on the mediawiki's Wacom Tablet Configuration:  [https://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Category:HOWTO](https://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Category:HOWTO) or at the [Bamboo P & T HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562") attached to posts #1 & #2.  Although the xsetwacom interface will probably change with the arrival of xf86-input-wacom 0.10-11 next week.

---

