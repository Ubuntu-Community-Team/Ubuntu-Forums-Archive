---
title: "Toshiba Satellite screen problem on suspend/hibernate"
date: 2007-07-10
forum: Hardware &amp; Laptops
---

### Post by nimajiman on 2007-07-10
Hi,

It seems this problem comes up a bit but I haven't found an answer anywhere that helps, so I'll bring it up again. I have a Toshiba Satellite A100 running Ubuntu Feisty. Everything seems to work fine so far except for suspend and hibernate. It will do these ok but when resuming it seems there is a problem restarting gdm or X. Not sure exactly where the problem is but I usually get just a black screen, or sometimes can see my mouse cursor over just a black screen.

When I press Ctl ALt Backspace it will return to my login screen and everything is fine from there with the screen working again, but obviously I don't want to have to lose everything I have open every time it goes into suspend.

Any ideas?

---

### Post by godvalve on 2007-10-23
Just upgraded to Gusty Gibbon and I'm still having this problem.

I hit hibernate and the screen goes black with a blinking cursor in the upper left corner of the screen. The machine doesn't actually enter reduced mode.

---

### Post by Ambiguity on 2007-10-23
I have a toshiba m40 and I have the same problem. It worked occasionally in Fiesty, but in Gutsy it displays the black screen as described above.

When it did enter hibernate/suspend in Fiesty, it would always resume displaying a HAL hibernation error bubble.

---

### Post by Ambiguity on 2007-10-28
I found that after removing "hibernate" from synaptic package manager my computer gets closer to being able to go on standby. The screen actually turns off, as does the computer but it is not off...pressing the power button to turn it on does not work and it has to be reset. Hibernate still does the blinking thing.

---

### Post by kaston on 2007-12-13
i have a satellite A100 VA9 and i have the same problem.   i can go into suspend or hibernate mode ok, but when i raise the lid or move the mouse to try and wake up i just get a blank screen.  the only thing i can do is to do a hard shutdown and restart.  this was a problem after i went from vista back to xp too.  anyone find a solution yet?

---

### Post by Peter09 on 2007-12-13
I installed 'powersaved' from the repositories for my Toshiba. Works ok, minor probs but in the main a success.

---

