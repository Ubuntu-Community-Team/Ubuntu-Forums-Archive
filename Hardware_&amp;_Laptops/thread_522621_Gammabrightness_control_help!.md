---
title: "Gamma/brightness control help!"
date: 2007-08-10
forum: Hardware &amp; Laptops
---

### Post by speaker219 on 2007-08-10
Can anyone help me with this?
on windows, i have a utility to change gamma/brightness/contrast values, etc.
i want to do this on ubuntu. any help would be appreciated.
 i know of xgamma but i need something that can also control brightness (i know about the Fn+ combo, but this isn't what i'm talking about, its a brightness control utility that does something not hardware related [i think])

on windows, i have the following (see screenshot)

is there a ubuntu equivalent?

---

### Post by speaker219 on 2007-08-10
bump

---

### Post by speaker219 on 2007-08-10
gah...bump!

---

### Post by speaker219 on 2007-08-12
I FIXED IT!!! ;) Pardon me, i'm very excited ;)

Anyway, here's how i fixed it. I was googling and found this program:
[http://www.softpedia.com/get/Tweak/Video-Tweak/Gamma-Panel.shtml](http://www.softpedia.com/get/Tweak/Video-Tweak/Gamma-Panel.shtml)

It was a windows app, so last resort i figured, hey, i might as well sudo apt-get wine and try this out.

To my surprise, IT WORKED! I was able to control brightness, contrast, AND GAMMA!

GO WINE! (AND THE GUY THAT WROTE THE PROGRAM)
Hope this helps anybody with the same problem

---

### Post by chrisolof on 2007-08-29
Does anyone know what Wine is accessing to control gamma and how to control it without using a Windows program under Wine?  If Wine has access to the setting I'm assuming the value is in some configuration file somewhere.

I had a similar problem with Gamma - I was playing [The Ship]("http://www.theshiponline.com/") through Wine on Ubuntu and set the gamma as bright as it would go in the game to see well in dark places.  When I quit out of The Ship my desktop was glowing a heavenly white and I couldn't get anything accomplished.  Rebooting my machine didn't fix it.  So, I had to go back into the game through Wine and change the setting back to a normal value, which fixed it system-wide.

Also - when the game is run natively in Windows, gamma settings changed in games are kept in the games.  Is this possibly a bug in Wine where it is unable to make application-specific gamma changes that don't affect the whole system?

---

