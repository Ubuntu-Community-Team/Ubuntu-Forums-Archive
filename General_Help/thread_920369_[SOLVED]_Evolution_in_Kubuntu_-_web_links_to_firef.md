---
title: "[SOLVED] Evolution in Kubuntu - web links to firefox"
date: 2008-09-15
forum: General Help
---

### Post by eudemus on 2008-09-15
Hi,
I'm running Kubuntu 8.04 (KDE 3.5, not 4), and using Evolution for mail / calendar / etc..

Web links in Evolution don't open in my default browser (Firefox 2). In fact they don't open at all (despite a nice right-click option to "open link in browser") I've found a similar thread, where the solution involves changing the default app in the Gnome settings. But obviously, since I'm running KDE and not Gnome, that won't work for me. I already have FF-2 set as my default browser, but somehow this isn't picked up by Evolution, and there seems no obvious way to tell Evolution.

Can anyone help?

Cheers, Eudemus.

---

### Post by eudemus on 2008-09-16
OK. I solved this myself. Here were (in my very basic understanding) the steps necessary.

From this thread,
[http://www.go-evolution.org/FAQ#How_can_I_set_the_default_browser_in_Evolution.3F](http://www.go-evolution.org/FAQ#How_can_I_set_the_default_browser_in_Evolution.3F)

I used the following 
gconftool-2 -R /desktop/gnome/url-handlers/http
gconftool-2 -R /desktop/gnome/url-handlers/https

to ascertain that evolution seemed to be looking for firefox at /usr/bin/firefox. It didn't find it there because I'm using firefox-2.

The above link contains instructions about how to point evolution in a different direction to look for firefox-2, but I thought it would be simpler to create a "symbolic link" so that when it looks for firefox, it is redirected to firefox-2.
(In fact, the file /usr/bin/firefox-2 is itself just such a symbolic link - it points to /usr/lib/firefox/firefox-2)

So, the solution was:
sudo ln -s /usr/lib/firefox/firefox-2 /usr/bin/firefox

Now, in principle, any program that goes looking for firefox will find firefox-2.

Cheers, Eudemus

---

