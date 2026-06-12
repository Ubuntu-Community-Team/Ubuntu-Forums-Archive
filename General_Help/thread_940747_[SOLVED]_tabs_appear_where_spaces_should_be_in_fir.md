---
title: "[SOLVED] tabs appear where spaces should be in firefox"
date: 2008-10-07
forum: General Help
---

### Post by mullenrbock on 2008-10-07
i don't know how i did it, but even as i'm typing, when i press the spacebar it looks as if i'm inserting tabs instead. even in the firefox menus and in my bookmarks even the preferences window, everything, i mean EVERYTHING in firefox has a tab where a space should be. i don't know what exactly happened, i was messing around with emacs in a terminal in the foreground, and i think i accidentally switched to the firefox window with a key combination and now everything is spread out. i mean, it's not horrible, it's just really annoying to see each word spread out so far... thanks for any help!

---

### Post by geirha on 2008-10-07
Never encountered that before. Try typing **about:config** in the address field, and look at the settings in bold (settings that are bold are set to something other than default). Anyone of those settings regarding spacing?

---

### Post by mullenrbock on 2008-10-07
i'm looking around, i don't see anything in fonts that would affect the spacing...

---

### Post by mullenrbock on 2008-10-07
ok, it turns out that ALL of my browsers are doing this, galeon, epiphany, and firefox. the only one that doesn't is dillo. i couldnt find anything in about:config that changed this problem...

---

### Post by mullenrbock on 2008-10-08
is anyone else having this problem at all? also, i think it cause flash to have no sound...

---

### Post by geirha on 2008-10-08
Have you changed fonts lately? Try changing some fonts in System -> Preferences -> Apperance -> [Fonts] ... Not sure if fonts can do this, but I don't have any other ideas.

---

### Post by mullenrbock on 2008-10-08
No, nothing. I'll just live with it for now, maybe reinstall with the 8.10 final release. Thanks anyway, though.

---

### Post by geirha on 2008-10-08
I just found this bug on launchpad: [https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/193108](https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/193108)

Seems ```
sudo aptitude purge pango-graphite
``` may fix things.
[quote=Chris Lawrence]I tracked this problem down on one of my Debian boxes; this may also apply to Ubuntu, but I'm not sure.

The culprit appears to be the pango-graphite package. If I purge it, the Exceptions and spacing bugs go away, suggesting that Firefox has no clue how to deal with the Graphite extensions to TrueType/OpenType fonts.[/quote]

---

### Post by mullenrbock on 2008-10-08
Oh wow, thank you! It works! I had pango installed to build the newest version of "nted". Thanks!

---

### Post by patryk77 on 2008-10-08
If Flash has no sound, it's probably because of PulseAudio.

Simply install Flash player 10 Beta, and everything should be ok.

It works perfectly on my box now.

---

### Post by MaddMatt on 2008-10-14
Thanks a bunch! This just happened to me as I had installed pango to help with compiling xnee. Such an odd problem! Cheers!

---

### Post by aska786 on 2008-10-14
Earn money for clicking The Ads [sign up]("http://bux.to/?r=aska786") Here

---

### Post by shekhark on 2008-11-05
Yup, removing the package works. :KS

---

