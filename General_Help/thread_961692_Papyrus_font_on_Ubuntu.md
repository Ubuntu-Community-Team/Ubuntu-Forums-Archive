---
title: "Papyrus font on Ubuntu"
date: 2008-10-28
forum: General Help
---

### Post by Spades_Neil on 2008-10-28
Pure and simple, I wish to install this windows Papyrus font on my Ubuntu computer.

Problem is, I don't even know how to install ANY fonts, much less Windows to Ubuntu ones. Not even sure if this is POSSIBLE. If not, can I get a font that LOOKS like Papyrus, and then just change the name of it so it appears as such in my web browser? :P

I already did a search of the threads and found nothing too helpful. Again, I still haven't memorized a lot of commands in Ubuntu, so a nice step-by-step method would be helpful.

You guys have yet to fail me. :)

---

### Post by Fretsejaz on 2008-12-13
I'd like to see this as well, working on the same issue and I'm really in the same boat.

---

### Post by ajcham on 2008-12-13
If it's a ttf font it'll work just fine in Ubuntu - just copy any fonts you want into the **.fonts** directory in your home.  (You may need to create .fonts first)

---

### Post by lensman3 on 2008-12-14
Fonts live in "/usr/share/fonts".  Copy them there with the font family name.  It would work for just copying them into default.  The CD that I have a bunch of fonts called "metalica" and found in a metalia directory.  I just copied the entire directory (as root) into the /usr/share/fonts.

Then restart the X window with a cntl-alt-backspace to restart the X11 system.  (You might have to reboot).  I started openoffice and looked under the fonts to see if the new font was installed.  My X11 windows "blinked" at me and they were "just" registered. 

Google "installing microsoft fonts on Linux". Lots of howto's, but get a very recent one.  Older instructions have to have a font server configured.

---

