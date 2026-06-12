---
title: "I broke GTK2"
date: 2008-08-31
forum: General Help
---

### Post by jonothesockpuppet on 2008-08-31
I'm not exactly a Linux veteran. I'm comfortable as long as I don't do anything stupid. Well, the other day I did something really, really stupid.

Trying to compile PHP_GTK2 from source, I accidentally (please don't scoff!) downloaded the tarball for the wrong thing.
I configured it. I made it. I changed to root (entered my password) and "make install"ed it.

Strangely, I didn't have my php extension.

However, much later I restarted the computer and I notice that everything looks much different now:
- most GTK apps produce strange GTK-related errors when run from the console, if they run at all
- my font is almost totally unreadable (about 4px high) in most applications
- in XFCE's native theme chooser, the only options are Raleigh and Default (both of which cause headaches) despite the fact that I have a great number of engines installed and visible in the theme directory.

It's my own stupid fault. This is why I had to sudo it.
I assume it's due to my accidentally compiling non-Ubuntu GTK?
Is there some way to fix this with/without the package manager?

I'd rather not reinstall. I can work around it for now without having an anyeurism.
I can't just adjust the font size or use a 3rd-party theme changer, because each app handles fonts slightly differently (ie, Firefox's chrome is all way too small but the web pages are all for some reason left at a sensible size)

ANY ideas, pointers, feedback... I welcome it all (although of course I would prefer a solution)
I may have already tried some of it but please please please suggest it anyway, just in case I've overlooked the obvious.
I purged a lot of packages including xserver-xorg, and reinstalled many more, but that did no help or harm to the system or my current problem, so far as I can tell.

Thanks much in advance!




immediate EDIT: WOW I chose a bad title for this. Maybe it could have been "I installed nonstandard GTK2" or something. I guess i performed an unsupported operation and won't be surprised if nobody will help ;)

---

### Post by TenPlus1 on 2008-08-31
You could try re-installing the botched package that you re-compiled...

Goto terminal and type:

sudo apt-get <package name> (e.g. gtk2-engines)

...and it will re-install it and hopefully fix the problem...

---

