---
title: "adjusting pointer speed acceleration@ mouse preference"
date: 2009-01-18
forum: Hardware
---

### Post by lydmrtnyng on 2009-01-18
Hi, im using Linux4One on my acer aspire one...

i was trying to adjust the mouse acceleration and sensitivity... but i had a problem because the acceleration keeps of going back to slow even though how many times i have adjusted it... while the sensitivity works fine...

can someone teach me how to solve this? i was thinking that there might be another way of adjusting the pointer speed besides from doing it from the mouse preference...

thank you in advance!

---

### Post by MichB74 on 2009-03-06
Hi,

I am now experiencing the same problem, did you find any solution in the mean time?

cheers

---

### Post by jigme on 2009-03-30
This is happening to me as well. I adjusted the acceleration and now it just rubber-bands back to 0% each time it's touched.

Mouse acceleration won't budge from 0%

Sam

---

### Post by jigme on 2009-03-30
> **jigme said:**
> This is happening to me as well. I adjusted the acceleration and now it just rubber-bands back to 0% each time it's touched.

Mouse acceleration won't budge from 0%

Sam

Workaround 'solution':
As root, I entered 

xset m 19/10 7

Seems to be ok now, although the mouse acceleration in the preferences section still displays 0% acceleration. 

Sam

---

### Post by jigme on 2009-05-03
Actually, that's not a fix. It's a workaround at best as it needs to be set each time the computer boots. When X first boots, the mouse works fine for a second or so, then gets nerfed. 

I wanna find a solution before I make it auto set each reboot.

---

### Post by levimendes on 2009-05-15
I've found a couple posts on this and thought I would chime in here as well.

Razer DeathAdder mouse. Both acceleration and sensitivity are set to slow and low, still too fast... pretty annoying really...

I've tried xset and even temporarily it doesn't seem to go slow enough...

---

### Post by johnsky on 2009-06-01
I'm experiencing the same issue.


Slider rubber bands back to 0.
Another forum suggested the workaround of editing /etc/X11/xorg.conf and changing the options of the min max and accel options manually.

Problem with this is you have to restart X every time you try a new value, and, well, it's a temporary solution at best. We still can't change the speed in the mouse settings.

Also, for those who aren't aware, the "dead zone" settings for your touchpad are available further down below "mouse" in "settings">"touchpad"


I really hope they're aware of this before SC2 exits Alpha.

---

