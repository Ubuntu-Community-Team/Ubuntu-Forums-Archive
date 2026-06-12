---
title: "Can't enable desktop effects on 2nd user account"
date: 2008-09-07
forum: General Help
---

### Post by angelsneverdie on 2008-09-07
everything works fine on my account, but i set one up for my wife, and when i try to enable the "extra" in the visual effects tab in the appearance preferences in her account it says it can not enable it.

i'm using an inspiron 6000 with ubuntu hardy.

---

### Post by talsemgeest on 2008-09-07
You might want to install compizconfig-settings-manager, see if you can change any settings from there.

Also, install fusion-icon and try to launch compiz from there. Both programs are in the repositories.

---

### Post by angelsneverdie on 2008-09-08
I had the manager installed - i can access it, change things, but it doesn't effect anything.  I'm away from an internet connection atm so I'll try "fusion-icon" when i get home.  I've also noticed that it isn't just the "extra visual effects" that won't enable, but also the "normal" setting.

---

### Post by angelsneverdie on 2008-09-08
If the computer is off, and I boot up into my wife's account, it will let me enable the settings - but when i switch back to my account the desktop effects are disabled.

so it is only letting me use desktop effects on the account i boot into . . .

the plot thickens.

---

### Post by talsemgeest on 2008-09-08
That is strange, but instead of letting edubuntu manage your desktop effects, you should do it yourself through those two packages. I would suggest running fusion-icon on startup, so that it will enable the effects for you. Plus, if you run it from the command line you can see what errors it is throwing up.

---

### Post by angelsneverdie on 2008-09-08
So i just realized that I tagged this as edubuntu . . i must have missclicked, because I meant to tag it as ubuntu.  

I can't try the fusion thing until i get home, but i'm really interested in a fix instead of a workaroung, as my wife is both blind and not very computer literate - so things just working is a big deal.  

We have it working on our desktop (it's the zoom magnifier that she needs which is part of the extra desktop effects).

any ideas?

---

### Post by silverglade00 on 2008-09-08
Have you tried using the screen magnifier with Orca? It should be installed by default. Go to System -> Preferences -> Assistive Technology in her account. There is also the Gnome Magnifier that you can try.

---

### Post by angelsneverdie on 2008-09-08
Yes, i've tried those, but what works best is the one where the entire screen gets zoomed in on.

---

### Post by talsemgeest on 2008-09-09
If you can set up fusion icon to autostart, you can set it to start compiz fusion automatically as well. I wouldn't really call that a workaround.

---

### Post by angelsneverdie on 2008-09-09
i don't want to get into a fight about semantics here . . .   i'll try to get the fusion icon to autostart - 

but does anyone have any ideas why it won't just let me enable the extra desktop effects?

---

### Post by angelsneverdie on 2008-09-10
I've tried the Compiz fusion icon and still no go.  I can open the settings manager and change things and all of that, but none of it works.  Whenever i try to enable the extra visual effects it says that it can't.

---

### Post by rustutzman on 2008-09-10
Are you using fast user switching or are you logging out of one account and then back into the other?

Russ

---

### Post by angelsneverdie on 2008-09-10
fast switching.  but i just tried logging out and into the other account and get the same problem.

---

### Post by angelsneverdie on 2008-09-15
bump

---

### Post by Skerit on 2009-02-04
A friend of mine (a new Ubuntu user) has the same problem. The first user to log in gets desktop effects.

This is very annoying, of course, since they both use Docky (which does not work without compositing)

---

### Post by talsemgeest on 2009-02-04
> **Skerit said:**
> A friend of mine (a new Ubuntu user) has the same problem. The first user to log in gets desktop effects.

This is very annoying, of course, since they both use Docky (which does not work without compositing)
You should start a new thread instead of resurrecting an old one. :)

---

### Post by Skerit on 2009-02-04
Hmm, I thought people preferred to not start a new thread, as long as another one concerning the same thing is still "loose"

---

### Post by talsemgeest on 2009-02-04
> **Skerit said:**
> Hmm, I thought people preferred to not start a new thread, as long as another one concerning the same thing is still "loose"
It has been 4 months since the last post, so it it preferable to start a new than bringing back a dead one. You will have a greater chance of getting help with a new thread.

---

