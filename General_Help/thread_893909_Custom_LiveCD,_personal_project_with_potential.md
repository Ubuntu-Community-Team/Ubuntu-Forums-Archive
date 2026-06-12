---
title: "Custom LiveCD, personal project with potential"
date: 2008-08-18
forum: General Help
---

### Post by user11 on 2008-08-18
In my college we have computers set-up for internet access only for students who wish to register online, view e-mail, or do other things on the web academically related. 

Unfortunately, the machines we got here are heavily bloated Windows internet boxes that barely function enough to load a web page. Roxio GoBack (for those un-ending pop-ups, clock screw-ups, long boot periods, and random shutdowns!), Norton anti-virus (for those expired subscription pop-ups that are admin locked!) Adaware (the new one with no features!) and of course, Windows automatic updates (for gobbling up all that unused ram and CPU, mix it with GoBack, and it will run every time!)

I was thinking, as an alternative to the GoBack (or as I like to call it, GoBack to the stone age) which is really the cause for most of the problems, why not just use a Live CD permanently? I considered this as a fun project to start with. 

I started with Xubuntu (8.04.1), because when I used the Ubuntu Live CD it was a little slow but it got there (the instructions below should also apply to Ubuntu if people wanna try, just use "gedit" instead of "mousepad").  I installed it on one of my older PCs I had laying around, and customized it to be a typical no-frills internet box (removing lots of apps and unused images). After slimming it down, I replaced the ever-so-erroneous Abiword with OOo word (had three errors in a row the first day I used it), and I swapped out Gnumeric too just to match up OOo.  I made it so it would auto-login with a black background so boot-up would be seamless. Made a few URL links on the desktop and I even copied the wallpaper from a school computer. I even adjusted the appearance to look more like XP so it doesn't look too alien to the average windows user.

After all that, I installed Remastersys. Remastersys made a nice compact ISO, but when I burned and booted it, it defaulted my login set-up. To solve this I edited:

sudo mousepad /etc/gdm/gdm.conf

and changed,

# Automatic login, if true the first attached screen will automatically logged

# in as user as set with AutomaticLogin key.

AutomaticLoginEnable=false

AutomaticLogin=

to,

# Automatic login, if true the first attached screen will automatically logged

# in as user as set with AutomaticLogin key.

AutomaticLoginEnable=true
AutomaticLogin=USERNAME

I also changed the default background to black, 

# Background settings for the standard greeter:

# Type can be 0=None, 1=Image & Color, 2=Color, 3=Image

#BackgroundType=2

#BackgroundImage=

#BackgroundScaleToFit=true

# The Standard greeter (gdmlogin) uses BackgroundColor as the background

# color, while the themed greeter (gdmgreeter) uses GraphicalThemedColor

# as the background color.

BackgroundColor=#dab082

GraphicalThemedColor=#dab082

to,

# Background settings for the standard greeter:

# Type can be 0=None, 1=Image & Color, 2=Color, 3=Image

#BackgroundType=0
#BackgroundImage=
2
#BackgroundScaleToFit=true

# The Standard greeter (gdmlogin) uses BackgroundColor as the background

# color, while the themed greeter (gdmgreeter) uses GraphicalThemedColor

# as the background color.

BackgroundColor=#000000
GraphicalThemedColor=#dab082

After that, the Live CD booted perfectly.

The only problem I have is the following,

1)ejects on shutdown, and asks to hit enter to continue

2)Time is wrong.

The time problem is really stubborn. In live boot, it is wrong no matter what I do with the HDD install, maybe defaulted to Africa timezone? I just want it to be New York and that's it. setting the computer to check time with local internet servers and setting the time zone does nothing, I even edited: 

sudo mousepad /etc/default/rcS

and changed UTC = false, but to no avail. Anyone now how I can edit the default time zone? Unlike Ubuntu, Xubuntu didn't give me the option to NOT go by UTC, during the first install,(even though regular Ubuntu does)  does this have something to do with it? Is there a way to adjust Remastersys to NOT delete etc/timezone?

Also any other suggestions are appreciated.

---

