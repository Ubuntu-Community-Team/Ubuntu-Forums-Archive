---
title: "I messed up my graphics plz help!"
date: 2010-04-11
forum: Hardware
---

### Post by Pabloincarnate on 2010-04-11
I've been using ubuntu on my laptop a while now but not really for gaming so i wanted to try with warcraft 3. The game would start but run very slow and flicker a lot. sum 1 told me that i should use the synaptic package manager to look for stuff relevant to my graphics card. **Seeing that my graphics card is an ATI, i had done a quick search (ati) for relevant packages.** needless to say that made things worse as compiz had stopped working and my laptop started running ubuntu in low graphics mode. 

**I have a DELL LATITUDE D600 with a Moblity Radeon 9000 graphics card**

At this moment, I only have the default jockey files because i screwed things up the first time........

I hope i posted this in the right place this time.....

---

### Post by stilling on 2010-04-11
> sudo dpkg-reconfigure xserver-xorg

you'll be guided to several steps where you can reconfigure your keyboard, mouse, display driver and screen resolution my suggestion is to go through those steps and, if your keyboard and mouse are correctly set, just don't change them, just leave them as they are with the display driver you should look for one called «nv» or, if you don't see it, just pick the one called «vesa», it usually works for any display and for me, it's the one that get's me out of trouble after that you can choose what you'll find to be the correct screen resolution when all this is done just logout (you don't have to restart, I think!) and hit Ctrl+Alt+F7 to return to the GUI interface (not terminal) hopefully you can manage the installation of the correct driver for your graphics card within Ubuntu GUI.

hope this helps you

---

### Post by Pabloincarnate on 2010-04-11
Thanx i'll see if this works

---

### Post by Pabloincarnate on 2010-04-11
i tried that but nothing happens after i enter my password. am i supposed to restart or something?

---

