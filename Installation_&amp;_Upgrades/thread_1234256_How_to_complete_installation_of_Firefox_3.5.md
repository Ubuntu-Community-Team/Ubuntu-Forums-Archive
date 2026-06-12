---
title: "How to complete installation of Firefox 3.5"
date: 2009-08-07
forum: Installation &amp; Upgrades
---

### Post by jcobban on 2009-08-07
I tried installing Firefox 3.5 using the Package Manager.  However after installing it I found that I could not invoke it through the normal icons in the Application Menu or on the task bar at the top of the screen.  Investigating I found that both of these invoked "firefox %u".  Issuing "which firefox" I found it invoked /usr/bin/firefox.  /usr/bin/firefox is a link to /usr/bin/firefox-3.0.  It seems to me that the installation of Firefox 3.5 should either have changed this link, or at least added a new icon into the application menu, so I could choose which browser to use.  I tried to manually correct the link in /usr/bin/firefox by:

cd /usr/bin
sudo rm firefox
sudo ln firefox-3.5 firefox

but this set /usr/bin/firefox to point directly at ../lib/firefox-3.5.2/firefox.sh.  Now when I try to invoke the application "firefox" I get "exec: 175: /usr/lib/firefox-3.5.2/firefox: not found"!  I fiddled around and finally got the link to work by issuing:

sudo ln -s firefox-3.5 firefox

This is way too much complexity to expect an ordinary user to deal with.

---

### Post by Partyboi2 on 2009-08-08
Hi, the easiest way to launch firefox 3.5 that was installed by Synaptic is to go to Applications>Internet>Shiretoko.

---

### Post by Nemo_bis on 2009-09-11
> **jcobban said:**
>  but this set /usr/bin/firefox to point directly at ../lib/firefox-3.5.2/firefox.sh.  Now when I try to invoke the application "firefox" I get "exec: 175: /usr/lib/firefox-3.5.2/firefox: not found"!  I fiddled around and finally got the link to work by issuing:

sudo ln -s firefox-3.5 firefox
Thank you! I had the same problem after synaptic installed a firefox-3.0 update overriding symbolic links.

> **jcobban said:**
> This is way too much complexity to expect an ordinary user to deal with.
I suppose that an ordinary user is supposed to use firefox-3.0 until Ubuntu 9.10 is released.

---

