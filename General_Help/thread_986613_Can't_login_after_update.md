---
title: "Can't login after update"
date: 2008-11-18
forum: General Help
---

### Post by J_Man on 2008-11-18
Not sure if this is the right place to post this.  I had a search of the forums and couldn't find anything very helpful.  I'm pretty new to Linux and most of it went straight over my head, but I'm keen to try stuff out.

Ubuntu just updated itself after not being used for a while, and required a restart.  I dutifully restarted but when I was presented with the login screen, it would not accept my credentials, saying "incorrect username or pass".  I'm 100% certain I have these correct.  I tried pressing ctrl+alt+f2 and logging in using the console, which seemed to work, but being quite new to Linux I have no idea what to do from there.  Does anyone have any suggestions?

I'm running Hardy Heron 32-bit.

---

### Post by Th3Professor on 2008-11-18
> **J_Man said:**
> Not sure if this is the right place to post this.  I had a search of the forums and couldn't find anything very helpful.  I'm pretty new to Linux and most of it went straight over my head, but I'm keen to try stuff out.

Ubuntu just updated itself after not being used for a while, and required a restart.  I dutifully restarted but when I was presented with the login screen, it would not accept my credentials, saying "incorrect username or pass".  I'm 100% certain I have these correct.  I tried pressing ctrl+alt+f2 and logging in using the console, which seemed to work, but being quite new to Linux I have no idea what to do from there.  Does anyone have any suggestions?

I'm running Hardy Heron 32-bit.

1. Reboot
2. Select "recovery" option in boot menu
3. Go to command line
4. passwd (username)

---

### Post by J_Man on 2008-11-19
Thanks for the advice, I've tried this out but to no avail.  As I said, my user/pass works fine from the console by pressing ctrl+alt+f2, so it seems to be a problem with the graphical login screen rather than my password actually being changed.

:(

---

### Post by J_Man on 2008-11-19
Well I've semi-solved the problem...  For some reason the update has made the login screen use a different keyboard layout, meaning that some of the special characters I use in my password are in a different position.  I solved this by changing my password to something simpler, but I'd rather not have to do this.  The keyboard layout is the correct one for use everywhere except the login screen, and I can even login through the terminal using the correct layout.  It's just the login screen that's the problem.  Does anyone have any idea what to do about this, and why it occurred in the first place?

---

### Post by J_Man on 2008-11-19
Upgraded to Intrepid Ibex, seems to have fixed the problem.

---

### Post by Th3Professor on 2008-11-19
cool :)

---

