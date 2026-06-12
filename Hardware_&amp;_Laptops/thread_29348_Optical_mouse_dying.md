---
title: "Optical mouse dying"
date: 2005-04-23
forum: Hardware &amp; Laptops
---

### Post by JonahRowley on 2005-04-23
I have a cheap Micro Innovations optical mouse on PS/2.  It works fine in Windows, and on Knoppix (older version, running 2.4 kernel), but not on Hoary.  In fact, it not only doesn't work, but if I move the mouse while Linux is running, the light goes off and it dies completely until next cold boot.  While X is running, if I push a mouse button, it moves the cursor to the top right of the screen.

I searched the forums and google, but I couldn't find anyone with the same problem (but it's late so maybe I'm not too good at the keyword dance).  The only other related problem I could find was references to 2.6 difficulties handling mice on KVM switches, and adding "proto=exps" to psmouse's options fixes this.  Perhaps this very cheap mouse only uses the EXPS/2 protocol?  Just a guess, if I have time tonight, I'll try it out.

---

### Post by codejunkie on 2005-04-24
i know this is not any help but im using hoary and Micro Innovations mouse and i've had no problems with it did you do a standard install or did you have to disable any thing for it to install, or use any specific boot options?

---

### Post by JonahRowley on 2005-04-24
This is a default install of Hoary.  I've only changed one thing, taking 1600x1200 out of the X config, but that shouldn't affect the mouse.  The mouse dies as soon as psmouse is loaded, and can't be revived.

---

### Post by codejunkie on 2005-04-24
[QUOTE=JonahRowley]This is a default install of Hoary.  I've only changed one thing, taking 1600x1200 out of the X config, but that shouldn't affect the mouse.  The mouse dies as soon as psmouse is loaded, and can't be revived.[/QUOTE]

you could try hitting ctrl+c right before it loads psmouse disabling that may work if that module is causeing the problem but i can't be sure.

---

### Post by JonahRowley on 2005-04-25
Not loading psmouse is about as useful as not loading your video drivers :P  Sure, if I don't load psmouse, the mouse doesn't die, but I can't use it anyway..

---

