---
title: "Google Earth illegible"
date: 2008-07-21
forum: General Help
---

### Post by SusieSA on 2008-07-21
Hi

I'm trying to get Google Earth working on my pc.  When I install it and try to run it, the file menus are illegible.  See attachment.  I know that it's says File.. Edit... etc, but I really can't read it.  

Also, if I type something in the search box, nothing is returned.

Any ideas?

Thank you
SusieSA

---

### Post by Potatoj316 on 2008-07-21
Strange, did you install from the repos or the google earth sire?

---

### Post by SusieSA on 2008-07-21
I downloaded it from the Google Earth Site.  I'm a real newbie here - what are the repos?

---

### Post by michaeltobin on 2008-07-21
im a noob too, and have the same problem:confused:

---

### Post by Potatoj316 on 2008-07-21
repos-repositories, using synaptic package manager, aptitude, or apt-get (aptitude is best but synaptic is easiest)  try removing it to the best of your ability. I think its something like make remove or make unistall then in a terminal type
```
aptitude search google
sudo aptitude install GOOGLEEARCH
``` (im not sure what the package is called exactly so you will have to change that GOOGLEEARTH to the package that the search found)enter your password when it asks (you wont see it being entered though) then hit enter when done with password.  You might have 2 google earths now if you didnt un install the old one.

---

### Post by tjwoosta on 2008-07-21
there is a google earth package availible in the repository, but to be honest it probably wont make any difference


i have tried every single goolge earth linux package i could find but i still have the same problems that you are having now on my laptop

(it works fine on all my other computers so i think it has something to do with the graphics card)

---

### Post by SusieSA on 2008-07-22
> **tjwoosta said:**
> there is a google earth package availible in the repository, but to be honest it probably wont make any difference


i have tried every single goolge earth linux package i could find but i still have the same problems that you are having now on my laptop

(it works fine on all my other computers so i think it has something to do with the graphics card)

Many thanks for your help T.  Think it must be my graphics card, so will get outside help.  Suzie

---

### Post by ramjet_1953 on 2008-07-22
Google Earth has a problem with Compiz Fusion.

Just navigate to [COLOR="Blue"]System>Preferences>Appearance[/COLOR]

When the window opens, click on the [COLOR="Blue"]Visual Effects Tab[/COLOR]

Select [COLOR="Blue"]None[/COLOR].

After it has done it's thing, click on [COLOR="Blue"]Close[/COLOR].

Now try running Google Earth again. 

I think you will find it will be OK.

Regards,
Roger :cool:

---

### Post by tjwoosta on 2008-07-22
> 
Google Earth has a problem with Compiz Fusion.

Just navigate to System>Preferences>Appearance

When the window opens, click on the Visual Effects Tab

Select None.

After it has done it's thing, click on Close.

Now try running Google Earth again.

I think you will find it will be OK.


o my god

your right

(i never thought about it but my laptop is the only one of my computers running compiz and its also the only one google earth wouldnt work on)

it works without compiz, thank you

---

