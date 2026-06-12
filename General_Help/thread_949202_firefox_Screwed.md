---
title: "firefox Screwed"
date: 2008-10-15
forum: General Help
---

### Post by ruipalmeira on 2008-10-15
hey there after installing and testing openbox, my firefox installation began to act strangely... text is all wide and stuff... error console gives me errors in almost every CSS property of the main page "http://start.ubuntu.com/8.04/", I attached a sshot of firefox so you can understand my problem....

thanks in advance

PS: i tried to uninstall firefox and installing it again.. no shot.. firefox 2 doesn't seem to be affected by this.

---

### Post by patrickballeux on 2008-10-15
> **ruipalmeira said:**
> hey there after installing and testing openbox, my firefox installation began to act strangely... text is all wide and stuff... error console gives me errors in almost every CSS property of the main page "http://start.ubuntu.com/8.04/", I attached a sshot of firefox so you can understand my problem....

thanks in advance

PS: i tried to uninstall firefox and installing it again.. no shot.. firefox 2 doesn't seem to be affected by this.

To reset you settings, simply rename the firefox folder in your home directory.  It is called ".mozilla/firefox"

You can delete it, but I would suggest renaming so you'll be able to import your favorites...

```
mv ~/.mozilla/firefox ~/.mozilla/firefoxbackup 
```

Good luck

---

### Post by ruipalmeira on 2008-10-16
that didn't help either... in attachment goes an image of firefox logging in ubuntu forums... so you can see the real problem with this... i have it too in epiphany for example.. but not in other apps such as terminal, rhythmbox, audacious... just this epiphany and firefox3 have the same problem .... appreciate help please

the fonts are right.. but the spaces are huge...

---

### Post by patrickballeux on 2008-10-16
> **ruipalmeira said:**
> that didn't help either... in attachment goes an image of firefox logging in ubuntu forums... so you can see the real problem with this... i have it too in epiphany for example.. but not in other apps such as terminal, rhythmbox, audacious... just this epiphany and firefox3 have the same problem .... appreciate help please

the fonts are right.. but the spaces are huge...

Then there is something common between Firefox and Epiphani (Gecko libraries?)...  Look at the dependencies of both, and re-install any libraries that they share...  

You can see that by looking in Synpatic, find the Firefox package, and in the properties, see the Dependency tab...

---

### Post by ruipalmeira on 2008-10-17
thanks... just formated ubuntu ... now it's fixed... no more bashing my head torwards the monitor for such silly thing ;)

---

