---
title: "Toshiba Satellite L505-LS5010 does not respond to keyboard/mouse input"
date: 2010-02-19
forum: Hardware
---

### Post by terminalmancer on 2010-02-19
Hi all -- apologies if this is dealt somewhere else but I haven't been able to find anything that seems remotely related.

I purchased a Toshiba Satellite hoping to install Linux on it and as far as I can tell most of the critical hardware is Ubuntu-compatible. But when I try to install or run the LIveCD, Ubuntu doesn't accept keyboard or mouse input! It's very frustrating.

I've tried both built-in and USB versions of both keyboards and mice to no effect. Has anyone seen anything like this before? Has anyone *solved* anything like this before?

Any advice would be appreciated. Thanks!

---

### Post by quixote on 2010-02-21
Something about the X system is not setting up the keyboard and mouse correctly.  If you get the right entries and/or drivers, it'll work.  In Ye Olde Days, that involved editing /etc/X11/xorg.conf.  In karmic, they've changed how that's handled and I have no clue. :(  Try searching for "Toshiba Satellite" "xkb" and possibly just in case "xorg.conf" and see if anything comes up.

---

### Post by mark.ad on 2010-03-14
I have the same issue as the OP.  When installing via the live cd there is no keyboard or mouse input being accepted.  I have the Toshiba Satellite L505D-LS5002.  I too have been scouring google and have mainly just found people talking about router problems.  I have a 64 bit system and was just installing the 32 bit version of ubuntu, but from the little I know that shouldn't really make a difference.  

I will keep searching, but any ideas in the mean time would be great, or perhaps a response from the OP as to what ever happened with his situation.

---

### Post by terminalmancer on 2010-03-14
> **mark.ad said:**
> I have the same issue as the OP.  When installing via the live cd there is no keyboard or mouse input being accepted.  I have the Toshiba Satellite L505D-LS5002.  I too have been scouring google and have mainly just found people talking about router problems.  I have a 64 bit system and was just installing the 32 bit version of ubuntu, but from the little I know that shouldn't really make a difference.  

I will keep searching, but any ideas in the mean time would be great, or perhaps a response from the OP as to what ever happened with his situation.

Apologies for not following up -- it sounds like I'm going to have to spend an inordinate amount of time messing around with config files in a LiveCD. Unfortunately I haven't really had time to mess around, so I couldn't tell you what works and what hasn't. I've just been sticking with Windows.

---

### Post by mark.ad on 2010-03-14
> **terminalmancer said:**
> Apologies for not following up -- it sounds like I'm going to have to spend an inordinate amount of time messing around with config files in a LiveCD. Unfortunately I haven't really had time to mess around, so I couldn't tell you what works and what hasn't. I've just been sticking with Windows.

Thank you for the quick reply.  It's good to know that there may be a way to fix it.  I'm a neophyte for the time being, but I will continue to look into this as well.  If I find a solution or any significant information, I'll be sure to update this thread.

until then, happy tinkering :-)

---

### Post by colinwhipple on 2010-03-15
Look here:

[http://ubuntuforums.org/showthread.php?t=1301101&highlight=l505d](http://ubuntuforums.org/showthread.php?t=1301101&highlight=l505d)

---

