---
title: "xrandr extension / fglrx driver issues"
date: 2008-04-25
forum: Hardware
---

### Post by gadget_hacker on 2008-04-25
I just finished upgrading to 8.04 and some display properties are not functioning properly.  I have a z61m thinkpad with an ati x1400 card and an external monitor.  

1st problem - Although I checked to use the restricted drivers (xorg-fglrx) from the hardware drivers window, when I do a fglrxinfo, I get this:

display: :1.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org]("http://www.mesa3d.org")
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (2.1 Mesa 7.0.3)

I'm guessing I'm not actually using the fglrx driver.
2nd problem - when I go to screen resolution, I get an error message of "The X Server does not support the XRandR extension.  Runtime resolution changes to the display size are not available."  From what I've been reading, I guess that has something to do with my external monitor, right?  

What should I do?  I added my current xorg.conf to the thread.
I would appreciate any help.  I posted because most people's problems were with compiz, but mine is working fine, actually.> 

---

### Post by gadget_hacker on 2008-04-28
can someone please help.

---

### Post by thevoidreturns on 2008-04-28
Also suffering same issue

---

### Post by gadget_hacker on 2008-04-28
I have been playing with the xorg.conf file after searching endlessly to find a solution to this problem.  I found that adding this into my xorg.conf file:

Section "ServerFlags"
        Option "RandR" "on"
EndSection

Seemed to fix my problem with using the screen resolution program.  However, by putting that into my conf file, I lost the ability to use compiz and my laptop monitor is no longer recognized and stays blank.

Does anyone have any ideas?

---

### Post by gadget_hacker on 2008-04-28
bump

---

### Post by turn1200 on 2008-04-28
Remove the package xserver-xgl

Explanation: If you installed this previously in order to make compiz work, it will not allow direct rendering on your display. You can check out if this is what it causing the problem by running 
DISPLAY=:0 glxinfo | grep renderIf it returns an ATI renderer, it means that xgl is being displayed indirectly on the display 1. (Taken from [1]) 
Warning: This might make your compiz stop working as it is configured to use XGl. A solution might be to run the Envy script in order to configure compiz. 
Also, if Compiz stopped working due to "Composite" problem, check that 
Section "Extensions"
	Option		"Composite"	"Enable"
EndSection
is set.

---

### Post by gadget_hacker on 2008-04-28
I can't believe I'm responding to my own post and still no one seems to be offering any help.  I found that with the attatched xorg.conf file in the post, I can fix my resolution problems with the xrandr -s command.  That way, I can keep compiz and have the resolution needed to use both screens.  I just don't have any dual screen settings.  It's pretty much a cloned output.  I really wish someone would see this thread and be able to help me restore all of the goodness that I had with 7.10. I've seriously considered downgrading, which I would never have thought would have been a possibility with Ubuntu, only with Vista!  Maybe someone can help me re-affirm my faith by giving me some tips?  I'm pretty much shooting in the dark right now.

---

### Post by gadget_hacker on 2008-04-28
thank you so much for responding.  I was pulling my hair out, because I'm not good at this sort of stuff.  When I do that command, I get:

direct rendering: Yes
OpenGL renderer string: ATI Mobility Radeon X1400

So I guess my next question would be what is the envy script used to configure compiz?

also, my extensions section looks like this:

Section "Extensions"
        Option          "Composite"     "0"
EndSection

Should I try and set composite to "1" first, and then try the envy script if that doesn't solve my problem?

---

### Post by turn1200 on 2008-04-28
> **gadget_hacker said:**
> thank you so much for responding.  I was pulling my hair out, because I'm not good at this sort of stuff.  When I do that command, I get:

direct rendering: Yes
OpenGL renderer string: ATI Mobility Radeon X1400

So I guess my next question would be what is the envy script used to configure compiz?

also, my extensions section looks like this:

Section "Extensions"
        Option          "Composite"     "0"
EndSection

Should I try and set composite to "1" first, and then try the envy script if that doesn't solve my problem?

I was having the problem of it not using the ATI which removing the package xserver-xgl fixed.  It's likely you have that from setting up beryl / compiz so then to get that working change the "0" to "Enable" for your composite setting.

I myself have the problem when I login I need to type xrandr -s 0 to get both screens going.  Some other's have had the problem too and I'm not sure what the solution is.  Of course at the login screen it works fine until I log in lol.

---

### Post by gadget_hacker on 2008-04-28
thank you so much turn1200.  Removing the xserver-xgl package and setting composite to ¨enable¨ really did the trick.  Everything seems to be running a lot smoother now.  I only wish I could use both monitors independently, instead of just cloned output.  Ubuntu only sees one screen.  I guess beggers can´t be choosers.  Have you gotten two monitors to really work?

---

### Post by turn1200 on 2008-05-02
Yes.  My problem now is that I can't get the resolution on each monitor to 1280x1024.  They cap at 1024x768.  As far as your problem, I'm trying to remember what I did.  I think I ran krandrtray and set the display options there.  I was hesisitant to try this initially because I had problems when I ran that app on Fiesty.  However, it seems to work ok with Gutsy.

Anyone know how to get above 2048x768 resolution for the combined monitors?

---

### Post by gadget_hacker on 2008-05-02
That´s interesting, because I´m not having a problem setting higher resolutions.  My external monitor only goes up to 1280x1024, so that´s what I have my resolution set to.  My initial problem was that I could not lower the resolution from 1600x1200.  I just can´t actually have a spanning desktop right now.  I tried the aticonfig --initial=dual-head command, but it made no difference.  Well, I´m glad that I at least was able to get help getting a good resolution and compiz to work.  Thanks again!

---

