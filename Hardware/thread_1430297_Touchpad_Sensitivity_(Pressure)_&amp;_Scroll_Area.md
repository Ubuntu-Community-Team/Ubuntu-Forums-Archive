---
title: "Touchpad Sensitivity (Pressure) &amp; Scroll Area"
date: 2010-03-15
forum: Hardware
---

### Post by kazakore on 2010-03-15
I am using a Clevo D901C with its built in touchpad but having dificulties getting it to work how I like.

Initially tried with just the standard Mouse Preferences. Got it better, was initially too fast and zipping across the screen so fast almost impossible to select anything (strangely adjusting this made it VERY slow in Windows when I first rebooted back into my WinXP partition.)

It is far to sensitive to pressure though. Sensitivity setting seems to do nothing whatsoever!

I have now installed the Touchpad Preferences. This gives a few more options but still Sensitivity does nothing as far a I can tell.

What I want it to do is change how much pressure is needed to activate the touchpad (I have this option in Windows.) Currently I move the cursor over say a button, take my finger off and the cursor may jump up to an inch in some direction. Really irritating! Also sometimes opens windows or focuses on other program when trying to click on something in the Dock. Makes highlighting text or double clicking with the pad, rather than its button, nigh on impossible! 

Is there anything I can do about this? (Got it as close to usable as possible with the Acceleration set low and min and max at extents but far from perfect.)

Edge Cursor Movement works (which I don't particularly like except when dragging) but Edge Scrolling will not. Any way to get Edge Scrolling working as it is something I find essential to comfortable use.


Also

---

### Post by kazakore on 2010-03-15
Even though I included it in the title I forgot the final annoyance.

Is there any way to set the zone/area used by the scrolling? Currently it takes up about a third of the rhs of my touchpad, which is FAR too much! Like the fact you can travel over this once you are moving though.

---

### Post by kazakore on 2010-03-15
OK I can just about get past the Edge Scrolling by using Circular Scrolling, although I think it will take me a bit of time to get used to.

Still really need to be able to edit the size of the area this is activated from as feel it's a bit large.


But my most important point is still pressure sensitivity of the touchpad! Is there no solution for this?

---

### Post by phillipjennings5 on 2010-03-16
yeah same here my touch pad right scrolling in in the middle of the keypad and its annoying as hell

---

### Post by ndefontenay on 2010-03-16
on Dell Studio the touchpad is rather large and very sensitive too. If I'm typing and my palms both hit the touchpad, my mouse starts jumping all other the screen. It is indeed irritating.

---

### Post by kazakore on 2010-03-16
SO no way to change in Ubuntu?

Realised it is the culprit for suddenly jumping windows after selecting one from the panel too. Scroll over your applications in panel will cycle through them. Rather annoying when it takes about a 1/3 of the pad and you often hit it by accident!

It is the one and only thing (well that and the fact I don't like any of the available wave editors but haven't put much effort into getting SoundForge to work well yet but I think I can overcome that one) that is making me almost tempted to just switch back to WinXP. Really is almost unusable, definitely wouldn't be able to do any graphics and animation with it!! Only been configuring the system so far and am finding it very grating!

---

### Post by kazakore on 2010-03-16
OK while still not perfect I've found a way to get slightly better results.

Remove Touchpad/gsynaptics and install gpointing-device-settings instead.

Has settings for Palm Touch, which has help a little with sensitivity and jerking position.

Although scroll area is still far larger than I like I would say it's a little smaller. Maybe 1/4 of the pad rather than 1/3.

Hope this can help you move towards a nicer set-up.

---

### Post by kazakore on 2010-03-17
Well after a days fairly heavy use have decided this is rather buggy. Using circular scroll to try circumvent the fact edge scrolling will not work and sometimes it seems to get stuck on. Completely remove hands from touchpad and when I touch again, no matter where, it will scroll until I tap it a once or twice.

Also think I might of just being hopeful about the area. Or if it is smaller only by such a small amount it doesn't really make that much difference!

Oh well, think it's back to the old system, in not Windows...

EDIT: It may of been my stupidity. Sure I set zone to be on the right again but checked the settings and it was the default of centre. Will see if it looses it or I misses setting it when I changes...

---

### Post by dE_logics on 2010-03-17
Are you sure it's a Synaptic touchpad?...It can be alps.

---

### Post by kazakore on 2010-03-18
Yep definitely Synaptic as that's what the Windows driver from the Clevo website are for.

---

### Post by kazakore on 2010-03-18
OK had to restart earlier due to network issues (gotta find a network manager that reconnects without having to restart! But that's a different matter) and can confirm that gpointing-device-settings forgets the zone set for circular scrolling. Quite annoying but at least I know now and the outer area isn't too huge...

---

### Post by jrssystemsnet on 2010-03-18
While it's not a direct answer to your concern (pressure sensitivity), you may find that just changing syndaemon settings will alleviate the problem, by making sure your palm doesn't do weird things on the touchpad while you type.

See my syndaemon how-to at [http://ubuntuwiki.net/index.php/Touchpad,_disabling_while_typing](http://ubuntuwiki.net/index.php/Touchpad,_disabling_while_typing).

---

### Post by kazakore on 2010-03-19
I know the disable while typing and personally don't like it.

It's more that when taking finger off it's not exactly smooth and your finger isn't a point, so part leaves earlier than another part of your finger tip so the mouse jumps in one direction or another.

Realised the problem with gpointing-device-settings is it doesn't same circular scrolling settings on a restart but with its setting I have pretty much got this particular problem to a bearable condition. Could be a little better and it would be nice to not have to reset my scroll zone every time I power on my laptop but it's just about workable.


The fact the zone, when using middle-side, takes up still far too much of the pad is a bit more annoying. Strange, as it I set it to right top/bottom corner the zone is almost too small to be usable (and just unnatural for me at the moment to always start in the same point whether scrolling up for down.)

---

