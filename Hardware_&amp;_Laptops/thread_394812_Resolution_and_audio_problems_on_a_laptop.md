---
title: "Resolution and audio problems on a laptop"
date: 2007-03-27
forum: Hardware &amp; Laptops
---

### Post by okke on 2007-03-27
I've got a Toshiba U200 laptop and I'm running Xubuntu 64 on it and I've bumped to a couple of problems. First of all I can't seem to get the correct widescreen resolution 1280x800 (now at 1024x768 ), I've tried lots of things but none of them seem to be doing any good.
I also have trouble getting any sound, didn't get beryl working, the suspend doesn't really work and probably the fingerprint reader won't work either. :( 

Any ideas to fix any of these?
:confused:

---

### Post by okke on 2007-03-28
Okay, for some strange reason I was able to fix the sound when I booted up Windows and un-muted it there. Strange huh, seems like it muted it on some hardware level. I still have problems on the other issues, any help?

---

### Post by okke on 2007-03-28
Help, anyone?
I also can't get direct rendering enabled on the gma 950.

---

### Post by queen_yoshi on 2007-03-28
Sounds like for the resolution you need to install 915resolution from the repos.

It will setup the 1280x800 resoution for you. I have to do the same with my lappy every install :D

---

### Post by okke on 2007-03-29
> **queen_yoshi said:**
> Sounds like for the resolution you need to install 915resolution from the repos.

It will setup the 1280x800 resoution for you. I have to do the same with my lappy every install :D

I can't get it working and the other problems won't go away either like the 3D support for the gma 950 wich is missing. Any ideas?

---

### Post by okke on 2007-03-30
So... In the display configurations there are just two options: "default" and "1024x768" and I think the default might actually be the correct 1280x800 I'm after but it won't show properly. If I choose it, the screen changes but to use the whole resolution I have to scroll around. Meaning that when the cursor is near the edges it scrolls the desktop. I'd like to squeeze it, how can I do that?
Later I tried changing to "vesa" drivers and the resolution worked just fine but I'd prefer the Intel drivers (i810) to get better performance elsewhere. Is it broken or why doesn't it work?

---

### Post by okke on 2007-04-01
Can't anyone really help me? Is this is a bug or where could the problem be?
I might just have to change back to XP :(

---

### Post by okke on 2007-04-01
Bump :(

---

### Post by jjordan on 2007-04-02
OK,

You are looking at some fairly advanced configuration problems here.  You are going to have to invest some time and effort to work through them but if you do you will learn quite a lot about Linux and what's going on in there.

First we need to figure out if you actually have an i915 video card,

a quick Google search indicates that your laptop has an i945 video card which is simply an improvement over the i915 (uses the same driver).

915resolution is in fact the key to getting your monitor working at its native resolution.  The problem is that 1280X800 is not one of the resolutions programmed into the bios of the i945 video card.  We have to smack it in the head and force it to acknowledge that it can run at that resolution.  915reolution attempts to do that on its own but does not always succeed.  I recommend you Google i915resolution and look for a good guide on how to set it up.  You will have to do a little command line work.  If you cannot figure it out, post back here and I will try to walk you through it.  I am at work right now and do not have access to my system.

-j

P.S. get things working well before you mess with beryl.

---

### Post by okke on 2007-04-02
> **jjordan said:**
> OK,

You are looking at some fairly advanced configuration problems here.  You are going to have to invest some time and effort to work through them but if you do you will learn quite a lot about Linux and what's going on in there.

First we need to figure out if you actually have an i915 video card,

a quick Google search indicates that your laptop has an i945 video card which is simply an improvement over the i915 (uses the same driver).

915resolution is in fact the key to getting your monitor working at its native resolution.  The problem is that 1280X800 is not one of the resolutions programmed into the bios of the i945 video card.  We have to smack it in the head and force it to acknowledge that it can run at that resolution.  915reolution attempts to do that on its own but does not always succeed.  I recommend you Google i915resolution and look for a good guide on how to set it up.  You will have to do a little command line work.  If you cannot figure it out, post back here and I will try to walk you through it.  I am at work right now and do not have access to my system.

-j

P.S. get things working well before you mess with beryl.

I have tried to use the 915resolution but I'm not able to change the resolution for some reason. Or perhaps I'm doing something wrong.

---

### Post by jjordan on 2007-04-03
Here is a good guide:

[http://absolutebeginner.wordpress.com/2006/08/20/absolute-beginner-guide-915resolution/](http://absolutebeginner.wordpress.com/2006/08/20/absolute-beginner-guide-915resolution/)

open a terminal
**sudo 915resolution 5c 1280 800**
close session
restart the X server (**ctrl+alt+bksp**)
check the config program you are using to set resolution or use:
**xrandr -q** 
**xrandr -s X** X is the number that appeared infront of 1280 800 from previous command.

-j

---

### Post by PlanetExpress on 2007-04-09
Hi,

I also have Toshiba U200-196 Laptop, using ubuntu and i experienced exactly the same problems. (1280x800 only possible using vesa driver, i810 only working in 1024x768 ) 

i915resolution solves some resolution problems on other intel gma notebooks, but didn't seem to work for me. (when i get it correctly, the resolution is already registered in the bios list, so this is NOT the problem, in fact the vesa driver can switch to 1280x800)

another issue is, that the i810 driver included in dapper really badly crashes whenever logging out or restarting the X-server (nothing than power off possible), but this seems to be solved in the newer versions of the driver e.g. the one in Feisty Fawn.

any ideas what to try next anyone? Direct Rendering would be sooo nice ;)

cheers

---

### Post by PlanetExpress on 2007-04-09
Finally got it working!

After i was really sure i was doing the right thing with 915resolution and the settings in my xorg.conf (which didn't work nevertheless) I found that there is an alternative implementation of the i810 driver in the xserver-xorg-video-i810-modesetting package (ubuntu-feisty)

i just installed it and now the xserver is able to switch to 1280x800 using the i810 display driver, enabling 'dri'.

hope this helps

---

