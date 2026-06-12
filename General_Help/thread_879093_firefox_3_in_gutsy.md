---
title: "firefox 3 in gutsy"
date: 2008-08-03
forum: General Help
---

### Post by chochem on 2008-08-03
Does anyone know how to get a decent firefox 3 build onto gutsy? (I returned to gutsy a month or two ago after hardy consistently dropped my usb connections) 

I have looked for repos (no luck), tried building it myself (worked, but no decent anti-aliasing) and switching to specialized builds (swiftweasel - nice enough but some very strange distortion artifacts appear on many pages). If any other gutsy users know of a means to get it, please let know. Googling gutsy firefox 3 just brings up results from last year offering all-in-one downloads of old betas :(

---

### Post by ptn107 on 2008-08-03
Enable 'gutsy-backports' in your sources.list file then do a *sudo apt-get update && sudo apt-get install firefox-3.0*

---

### Post by chochem on 2008-08-03
Well, even with backports enabled it's still at beta4 which - apart from not being up-to-date - looks nasty and non-anti-aliased...

EDIT: Cf. [the package page](http://64.233.183.104/search?q=cache:6aS5TEPjc_0J:packages.ubuntu.com/gutsy-backports/firefox-3.0+firefox+package+gutsy&hl=en&ct=clnk&cd=1)

---

### Post by zvacet on 2008-08-03
@ **chochem**

Try [Ubuntuzilla]("http://ubuntuzilla.wiki.sourceforge.net/")

---

### Post by aysiu on 2008-08-03
This is probably the quickest way to do it:
[http://www.psychocats.net/ubuntu/firefox#terminal](http://www.psychocats.net/ubuntu/firefox#terminal)

UbuntuZilla is a nice choice as well, as it checks the integrity of the download and also lets you know if new updates are available for Firefox.

---

### Post by chochem on 2008-08-03
Thanks for the suggestions, guys. Tthe ubuntuzilla version works nicely but is also somewhat lacking in the anti-aliasing department. I don't know if I'm missing something or other... Though the fact that swiftweasel's antia-aliasing works seem to counter that idea....

---

