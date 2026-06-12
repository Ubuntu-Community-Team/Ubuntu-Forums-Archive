---
title: "[SOLVED] Compiz caused white screen (joy!)"
date: 2008-11-05
forum: General Help
---

### Post by Kymus on 2008-11-05
Compiz has had a vendetta against me ever since 7.10 I think.. either way...

I tried enabling Compiz to see if it would magically work and instead I got a wonderful white screen of doom. Now, I've had this problem in the past and then the answer was to uninstall and then reinstall *fglrx*, however, I am unsure as to how I would do that in Gnome failsafe when the failsafe mode provides no menus.

So my questions are thus:

[LIST=1]
[*]How do I fix this white screen?
[*]If the solution is to uninstall and reinstall FGLRX in failsafe, then how do I do that without menu access?
[*](extra credit!) Is there a magic stick I beat Compiz with so that it will stop white screening me and just work? (yeah right)
[/LIST]

---

### Post by Kymus on 2008-11-05
bump.

---

### Post by overdrank on 2008-11-05
Hi and please do not bump your thread so quickly.
What is the model of the graphics card?
You may try and boot into recovery mode and use the xfix option to correct the graphics issues.
Recovery mode is usually the second choice from the grub.

---

### Post by Kymus on 2008-11-05
Sorry for the quick bumping; in my experience, once a topic is off the first page, it has always sunk into oblivion. Is there a time-frame that is more appropriate?

I'm using an ATI X800 GTO

I'm tried the X option in the recovery console; unfortunately, things were still the same >_<.

---

### Post by overdrank on 2008-11-05
> **Kymus said:**
> Sorry for the quick bumping; in my experience, once a topic is off the first page, it has always sunk into oblivion. Is there a time-frame that is more appropriate?

I'm using an ATI X800 GTO

I'm tried the X option in the recovery console; unfortunately, things were still the same >_<.

Hi and bumping your thread once in a 24 hr period is the standard. What version are you using now 8.04, 8.10?

As for the graphics you may try and at the white screen see if you can reach a virtual terminal with the ctrl, alt, F1 keys then login. You may then try and reconfigure you xorg with this command.```
sudo dpkg-reconfigure -phigh xserver-xorg
``` if the xfix option is not working for you.

---

### Post by Kymus on 2008-11-05
Will do; I will try it in a moment and report back, thanks :)

EDIT: I'm using 8.04 currently

---

### Post by Kymus on 2008-11-05
Well, now things are really interesting; I'm lucky like that I think.


It seems that xfix did get rid of the white screen... but now compiz is running in I guess what you could call "lite" mode and things are very laggy. I'll first try to disable compiz and we'll see if that does anything, then I'll try the other suggestion.

---

### Post by Kymus on 2008-11-05
Alright, it seems like after disabling Compiz, everything is working fine.

---

### Post by sdowney717 on 2008-11-05
upgrade to ibex.
It was the way I got my x1300 ati card to work with compiz. Like you I had nothing but the white screen while using hardy.
IBex also has the updated fglrx driver that works with xserver 1.5, xorg7.4
I got 3d acceleration back and can use google earth again.

I had not been able to use google earth or compiz the whole time I was running hardy and in desperation, upgraded to ibex alpha.

---

### Post by Kymus on 2008-11-05
Thanks for the suggestion! I was secretly hoping that upgrading to Ibex would magically fix it.

---

