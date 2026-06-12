---
title: "Login Screen is too Big"
date: 2008-08-07
forum: General Help
---

### Post by sandman3838 on 2008-08-07
Hello

My splash screen and desktop is just fine but my user sign-in screen is way to big!  Where can I adjust it?  What resolution would you recommend, should I use the desktop resolution of 1600x1024.

One other thing possibly related I don't know?
If I enable, show text on the splash screen is hangs for just a minute on Hardware Detection.  It used not to do that.  If there something I should run to re re-detect the hardware.

Note for my Video Driver installation I used ENVYG.  It did seem to load just fine weeks ago and the NVIDIA X control panel looks fine.

Video Card:
NVIDIA 7600GT 256mb
DDR3
Open GL2

Monitor:
Proview 2200W
Widescreen
Desktop resolution 1600x1024

Thanks All!

---

### Post by cdtech on 2008-08-07
You need to set the screen size for your login by setting it up within the xorg.conf file such as I did here:
```
 SubSection     "Display"
        Virtual     1440 900
        Depth       24
        Modes      "1440x900"
```
The Virtual is the login screen....

Hope this helps..........

---

### Post by sandman3838 on 2008-08-07
The login screen is fine now!
However once I'm at my desktop the Resolution stops at 1440 900?

The 1400x900 on the sign in screen is just great now but the desktop was at its default or 1600x1024 this in now unavailable.  The highest screen resolution stops at 1400x900.

Can I have both?

Thanks all!

---

### Post by cdtech on 2008-08-07
> **sandman3838 said:**
> The login screen is fine now!
However once I'm at my desktop the Resolution stops at 1440 900?

The 1400x900 on the sign in screen is just great now but the desktop was at its default or 1600x1024 this in now unavailable.  The highest screen resolution stops at 1400x900.

Can I have both?

Thanks all!

Sure you can. You didn't have to use the numbers I gave you.

Actually the complete section looks like this in my xorg.conf:
```
Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation NVIDIA Default Card"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "AddARGBVisuals" "True"
    Option         "NoLogo" "True"
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Virtual     1440 900
        Depth       24
        Modes      "1440x900" "1920x1440" "1920x1200" "1856x1392" "1680x1050" "1440x900@60" "1400x1050"  "1280x800@60" "1280x720@50" "1280x720@60" "1280x768@60" "1280x854" "1152x768@54" "1024x768" "800x600@60" "800x600@56" "1440x900" "1920x1440" "1920x1200" "1856x1392" "1680x1050" "1440x900@60" "1400x1050"  "1280x800@60" "1280x720@50" "1280x720@60" "1280x768@60" "1280x854" "1152x768@54" "800x600@60" "800x600@56"
    EndSubSection
EndSection
```

Thats just a subsection within a section........

**P.S.**
The first listed screen under "Modes" will be your default desktop resolution. Mine just happens to be "1440x900". You can put your resolution to be first and leave the rest....

---

### Post by sandman3838 on 2008-08-07
Thanks for you help!

The erg to fiddle was to great I couldn't wait!

While I was waiting for someone too reply I removed my NVIDIA drivers and reinstalled them through ENVYNG as suggested through another link here:
[http://ubuntuforums.org/showthread.p...a+driver+Hardy](http://ubuntuforums.org/showthread.p...a+driver+Hardy)

I also reset the xorg.conf as suggested in the other links above.

I think that a lot of the issues here was that there where three places to change the screen and resolution:
- APPS/OTHER/Screen & Resolutions
- APPS/SYSTEM/PREFERENCES/Screen Resolutions
- APPS/SYSTEM/ADMINISTRATION/NVIDIA X Server

I deactivated the first two and I'm letting NVIDIA X SERVER handle it.

Thank you one and all!

---

### Post by wallydallas on 2008-10-28
I have the same problem, and I got half way towards a fix.  But half a repair is almost worse.   What makes this hard is that so many people give advice without reading that their advice has been attempted by myself and others.   

for example:  I have the same problem as post #3.

I edited my file so it now reads like the code below.  The problem that remains is that the pre-logon screen size sets the limit to the maximum post-logon screen size.   In other words if I want my logon screen to be 640x480 so that it fits on the screen, then after I logon I can not use a resolution larger than 640x480.    

There are a lot of people with the same problem in 8.04.   I guess it will take a lot of users to report this, and then the code people will get their shorts in a bunch because some of the people do it in a nasty way.  I'm trying to be nice here.


```
Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        Defaultdepth    24
        SubSection "Display"
                Depth   24
                Virtual 1280    1024  
                Modes           "800x600@60"    "832x624@75"    "800x600@85"   $
        EndSubSection
EndSection
```


It is possible this only happens with video hardware that has an Nvidia chipset.  But that is a huge percentage of computers that have been built in the last 5 years.

---

### Post by rickg68905683u on 2008-12-12
It would be nice if the log on screen was locked to some
smaller (numbered) resolution that did not effect the resolution later. (Or so I've read.)
I've had this problem for years, and have stayed with MS because of such a dumb thing. (Can't log in!)
I've read the help messages in this and other forums, but currently have deleted the install, (again, as nothing helps).
(Or the help presented was not a new user friendly type.
Remember, my level is live CD and never run off the HD...)
As I see it, the log in screen is a sort of real mode res
and "should" default to something reasonable, (similar to what
Windows has when using safe mode.)
BTW: I "can" use the live CDs because they give a prompt
that allows to enter with Video safe mode (or some such wording.)
I've given up (again) on yet another years offering and am
waiting for this to be fixed.
This is meant to be constructive. It is my first post ever here.
Side note: A Puppy Linux live Cd works great with no special
settings or hoops to jump through.

---

