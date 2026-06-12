---
title: "ncurses line art rendering wrong in screen"
date: 2008-09-10
forum: General Help
---

### Post by Zebranky on 2008-09-10
On a fresh install of Hardy server, ncurses programs (tested with aptitude, finch, mc) render all line art as the â (a with caret) character when run inside screen. This does not happen outside a screen session. I've already tried changing LANG to "C" and "POSIX", and the problem still exists in both.

---

### Post by SATA on 2009-03-21
Im having the exact same issue.

What fixed it ? Or have you managed to work out what it was?

---

### Post by Tingles on 2010-08-09
I'm having the same problem with Finch (Pidgin 2.7.1) on Ubuntu 10.04 LTS.

It appears fine outside of screen in the CLI, but as soon as I try and launch it within Screen it has the garbled text where the line art borders should be.

I don't think this is a hardware issue because I just reformatted this box and it was running Slackware 13 and Finch worked fine in a screen.

Any thoughts?

---

### Post by Tingles on 2010-08-09
Holy crap I think I just fixed it.  For some reason, I had to change the settings in PuTTY (which is how I was accessing my box remotely) to use UTF8 instead of the default Translation.

Now the line drawing looks correct; however I'm still getting the random errors spit across the screen that say:

"(Finch:1226): pidgin-libnotify-plugin-DEBUG: Successfully wrote blacklist file to /home/<username>/.config/indicators/messages/applications-blacklist/pidgin-libnotifyMSN"

Strange.

---

### Post by lunalot on 2011-08-14
"holy crap" is right, tingles! that just fixed something that had been bothering me for 6 years! thanks!

---

