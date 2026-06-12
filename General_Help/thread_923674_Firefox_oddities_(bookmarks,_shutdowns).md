---
title: "Firefox oddities (bookmarks, shutdowns)"
date: 2008-09-18
forum: General Help
---

### Post by skunk12 on 2008-09-18
Hello. I got Ubuntu a few months back, running on a Gateway Phenom 9600 quad-core...but...yesterday, I came home, opened firefox, none of my bookmarks were there. Yet, if I typed stuff in the address bar, it popped up under like it was (firefox 3)...I restarted, it worked...stopped a while later, exported the html bookmarks, imported what I just exported, worked again..get home today, gone again, and now it closes if I go to tools > downloads or tools > add ons. I did a complete uninstall of firefox and several of the plugins, and reinstalled...still there...so...any idea what's going on?thanks...

---

### Post by peakshysteria on 2008-09-18
Please post OS (which Ubuntu version and 32 bit or 64 bit), FF version (32 bit or 64 bit) + additional version if any, addons installed and plugins installed.

---

### Post by skunk12 on 2008-09-18
Ubuntu 8.04, Firefox 3.0.1, both 64 bit, ubuntu firefox mods .5 extension, aquatint black gloss 3.0.1 theme, and I think that's it...but, I realized after posting this, apparently my harddrive was 100% full...after deleting some things, doing some moving, it's working now, and I have ~10 gig free..maybe that was it...who knows.

---

### Post by mb_webguy on 2008-09-18
Sounds like a corrupt profile to me.  This sometimes happens when extensions don't play nice with each other.

Back up your bookmarks and passwords (the [Password Exporter]("https://addons.mozilla.org/en-US/firefox/addon/2848") extension is handy for the latter), then close Firefox and either delete the .mozilla folder in your home directory, or create a new profile by typing "firefox -profilemanager" in the terminal.

EDIT:  Yes, a completely full hard drive could conceivably cause this too...

---

### Post by skunk12 on 2008-09-18
if it continues, I'll do that...but...I'm guessing it was my harddrive...>.> *stupid* thanks!

---

### Post by peakshysteria on 2008-09-18
If the problems persists check your addons for incompatibilities with other addons/plugins and:

[**Standard diagnostic - Firefox**]("http://kb.mozillazine.org/Standard_diagnostic_(Firefox)")

[**Firefox crashes**]("http://kb.mozillazine.org/Firefox_crashes")

And it would be easier to pinpoint your problem (if it persists) if you could give us the exact FF version and the name and versions of your addons. [Infolister]("https://addons.mozilla.org/en-US/firefox/addon/447") can help you acquire the info if you want it the fast and easy way :)

---

