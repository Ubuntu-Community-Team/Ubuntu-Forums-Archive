---
title: "Problems with HP 2230s"
date: 2008-12-20
forum: Hardware
---

### Post by CrazyDesi on 2008-12-20
Ok I am having a couple of problems with my HP 2230s.  One, the battery is draining about an hour earlier than in XP and the brightness does not work.  Does anyone know a work around?

---

### Post by xpeteyjtx on 2008-12-20
Hey, I am having the same issues with my 2530p. Battery life is lower than XP and brightness doesn't work.

CrazyDesi, I don't mean to hijack your post, but since we have very similar machines, I figured I could join in.

---

### Post by CrazyDesi on 2008-12-20
Yes that is fine.  I am very frustrated as I am a college student and don't have the money to buy another computer :(.

---

### Post by xpeteyjtx on 2008-12-20
> **CrazyDesi said:**
> Yes that is fine.  I am very frustrated as I am a college student and don't have the money to buy another computer :(.

I am a college student too. Why would you buy another computer? Just to run Ubuntu? I'm loving Ubuntu, but I would never spend $1500 more dollars just to run it.

But anyway...

my computer speakers also don't work. Headphones are good though.

Intel sl9400
4 gb ddr2
integrated 4500 graphics
running ubuntu 8.10 64-bit edition

---

### Post by xpeteyjtx on 2008-12-21
trying running

 xrandr --output LVDS --set BACKLIGHT_CONTROL native

Then try to adjust brightness using the "brightness applet".

That worked for me but when I adjust the brightness low enough, the whole screen goes off. So I need to mess with the limits somehow...

To improve battery life, try using powertop. It seems to help battery life for me, but the "tweaks" aren't permanent.

---

### Post by CrazyDesi on 2008-12-25
I'v tried to make the powertop functions permanent.  I moved the brightness as low as it will go in the BIOS when booting up.  I turned off dual core processor.  Same results though :(.  I just don't think Ubuntu has the battery life of Windows.

---

### Post by MATVIL on 2008-12-30
I have the exact problems with my HP2530p. No brightness, possibly lower battery life, no sound in speakers, but in headphones. The sound problems also seem to make disable Skype ("Problem with Audio playback"). 
My main concern is the sound problem. Any solution?

---

### Post by stembot on 2010-01-06
I've got a 2230s as well, and I'm befuddled as to how screen brightness is controlled.

I ran

[FONT="Courier New"]xrandr --output LVDS --set BACKLIGHT_CONTROL native[/FONT]

and then attempted to tweak the "brightness applet" (presumably the Brightness slider inside Power Management).

First, my screen would slowly dim itself, almost to the point of 0% brightness, and then slowly un-dim itself, but not back to 100% brightness.

I messed around with Power Management again, and have at least stabilised my brightness, but it's stuck at about 50%.  Which isn't terrible... but I don't think it's helping me save much power.

So, I want to get my brightness back to 100% since dimming it doesn't seem to save much power, if any.

---

