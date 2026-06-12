---
title: "Firefox is borked after an upgrade"
date: 2009-02-11
forum: Installation &amp; Upgrades
---

### Post by fredbird67 on 2009-02-11
Ubuntu Intrepid Ibex prompted me about half an hour ago to do an upgrade.  One of the packages to be upgraded was Firefox, to version 3.0.6.  After the installation was finished, I was then prompted to restart Firefox, which I did...and now all Firefox shows is a blank gray screen -- no browsing window, no address bar, no toolbar...not even a menubar or statusbar.  Nothing but a big gray blank space.

I've downloaded Epiphany for the time being and am using that (thank goodness Epiphany was available from the repos to bail me out here!).  I also just tried starting Firefox from the terminal and didn't get any error messages, either.  Does anyone know how to correct this or downgrade or something?

Thanx in advance,
Fred in St. Louis, MO USA

EDIT -- this is a problem only when I'm logged in as myself.  I just tried my wife's login and hers is OK.  Am I supposed to delete my ".mozilla" folder or something?

---

### Post by ottosykora on 2009-02-11
my kubuntu insisted on update too:

not only it seems to install some new kernel or what and it does not start any more with it, when finaly managed to start it by selecting older kernel, also firefox does not start any more at all and few other things seem to be strange.

---

### Post by fredbird67 on 2009-02-11
Well, my situation's not as bad as that -- mine only affects Firefox, and only on my account.  I haven't added any add-ons or bookmarked anything yet, though.  I'm tempted to copy the contents of my wife's .mozilla folder over to mine...

---

### Post by ottosykora on 2009-02-11
uninstalled only following:

firefox
meta package for the popular mozilla web browser


and now FF works again, but still says it is 306 version.

---

### Post by unixeducation on 2009-02-11
I just upgraded, too. After the Firefox install, I was prompted to restart the browser, but it wouldn't open again. I rebooted and Firefox started up okay, aside from the window size being tiny. Dragging it back out to normal size fixed it, and everything is back to normal now.

---

### Post by fredbird67 on 2009-02-11
Ottosykora, that did the trick for me! :-)  In my case though, I typed in "firefox" in Synaptic and removed firefox, firefox-3.0, firefox-3.0-branding, and ubufox, plus also removed my ".mozilla" folder in my home folder, reinstalled firefox and all of the aforementioned files it required as dependencies, and I'm happy to say that Firefox is now back in action! :)

PS -- I'm trying to mark this thread as solved.  I went under "thread tools", but I could swear that the "mark this thread as solved" item is missing!"  Does anyone know where that's gone to?

---

