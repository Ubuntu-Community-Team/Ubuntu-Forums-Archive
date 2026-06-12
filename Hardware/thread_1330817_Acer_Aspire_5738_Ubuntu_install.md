---
title: "Acer Aspire 5738 Ubuntu install"
date: 2009-11-18
forum: Hardware
---

### Post by tiddlydum on 2009-11-18
I'm trying to install ubuntu on my acer aspire 5738, but nothing. Tried x64, x86 and wubi, but it just loads a blank screen. Even in safe graphics mode. What happens is this:
Put the CD in and boot. Load the menu -> select install ubuntu. Screen flashes for a sec, then a cursor appears, then, nothing.
help?

*Update*
I think X is refusing to start: if you press the power button, it waits for a bit, then the disk drive pops out, and if you then pres enter, it shuts down. Gonna try text only install.

---

### Post by tiddlydum on 2009-11-19
Bump for free nades. Anyone had any ideas?

---

### Post by abmackay on 2009-11-19
FWIW, I have the same problem... on the same model computer (installed Ubuntu in Windows using Wubi).  I don't know much about Linux, so I'm a little lost.

Booting in recovery mode gave me the initial scrolling list of files being loaded, but then went to black without even the tantalizing drumbeats.

I found the following suggestion on the web:

Alt-Ctrl-F1 (I presume this should give me console)
#sudo dpkg-reconfigure xserver-xorg

But I can't even get a console to try it on, it just remained at a black screen :(

---

### Post by wilee-nilee on 2009-11-19
So your information is missing some key information like have you been able to install and it wont boot to the desk top or you just can't get the live cd to run. It is likely if the live cd that it wont run that you may have although unlikely have incompatible hardware, more likely is that it is a corrupted download or a bad burn. So If the case is a not running live cd make sure you have a good download burn it as a image not data at the lowest speed. I guess it would help if both of the posters gave this information and what cd burning programs did you use.

---

### Post by tiddlydum on 2009-11-19
Right, I've found more info, X isn't detecting the display. There's another (solved) [thread]("http://ubuntuforums.org/showthread.php?t=1307392&highlight=Acer+Aspire+5738") kicking about that should fix it, but to install( and fix) it, I just plugged in a different monitor.

---

### Post by tiddlydum on 2009-11-19
> **wilee-nilee said:**
> So your information is missing some key information like have you been able to install and it wont boot to the desk top or you just can't get the live cd to run. It is likely if the live cd that it wont run that you may have although unlikely have incompatible hardware, more likely is that it is a corrupted download or a bad burn. So If the case is a not running live cd make sure you have a good download burn it as a image not data at the lowest speed. I guess it would help if both of the posters gave this information and what cd burning programs did you use.
There is no disk burning error. The installation works fine if an external monitor is plugged in. X doesn't seem to be able to adjust for the laptop's internal display, but it does detect it.

---

### Post by wilee-nilee on 2009-11-19
> **tiddlydum said:**
> There is no disk burning error. The installation works fine if an external monitor is plugged in. X doesn't seem to be able to adjust for the laptop's internal display, but it does detect it.

I don't remember the command line way of adjusting this but somebody will probably help you with this. So are you able to go tp display in system-preference and see the dual monitor set up and click on the desk top what are your size choices.

---

### Post by tiddlydum on 2009-11-19
> **wilee-nilee said:**
> I don't remember the command line way of adjusting this but somebody will probably help you with this. So are you able to go tp display in system-preference and see the dual monitor set up and click on the desk top what are your size choices.

Doesn't work, I already tried this, monitor stays blank. Reinstalling to x86 rather than x64, and trying the solved thread's solution.

---

### Post by wilee-nilee on 2009-11-19
> **tiddlydum said:**
> Doesn't work, I already tried this, monitor stays blank. Reinstalling to x86 rather than x64, and trying the solved thread's solution.
Well I hope you find the solution.

---

### Post by tiddlydum on 2009-11-20
Right, found out how to do it, but grub's menu.lst is missing, so I can't fix it permenanently.

---

### Post by annasarp on 2009-12-22
Hey guys i am also using the same model laptop. Actually its the intel VGA problem. But after many searches i got the work around solution.
After installing Ubuntu when u start ur computer u will get the grub screen,
here press 'e' key 
after that enter the following (without quotes) "i915.modeset=0" before "quiet splash" string.
Once entered dont press enter key instead press ctrl+x key the system will boot into the gorgeous UBUNTU. 
Confirm me after doing this i will let u know how to add the above string in the grub file so that every time we need not repeat the above steps. :P

---

### Post by nechus on 2009-12-30
How weird!  Then I have to consider myself lucky, because I have the same laptop, which came preloaded with Linpus Linux, and Ubuntu installed wonderfully. Well, I used Super OS, actually. That could make a difference, I guess.

---

### Post by reddemon666 on 2010-01-30
@annasarp
Thanks, it worked absolutely fine. Could you let me know what I have to do to add it to the grub file?

---

