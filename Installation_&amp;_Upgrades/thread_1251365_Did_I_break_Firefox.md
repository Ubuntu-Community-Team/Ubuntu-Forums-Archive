---
title: "Did I break Firefox?"
date: 2009-08-27
forum: Installation &amp; Upgrades
---

### Post by rcbinwi on 2009-08-27
I am running Jaunty, and I tried to upgrade Firefox according to these instructions:
[http://www.1earthadventures.com/2009/07/01/the-net-now/installing-firefox-3-5-tar-bz2-on-ubuntu-9-04/](http://www.1earthadventures.com/2009/07/01/the-net-now/installing-firefox-3-5-tar-bz2-on-ubuntu-9-04/)

After I did so, Liferea and Thunderbird won't open links in Firefox.  (Did something happen to Gnome?)  When I reverted back to the old version of Firefox (I removed the new link to Firefox, I restored all the old link and file names, and removed the new Firefox folder from /usr/lib.)  This didn't help, and still, I can't get items to open in Firefox.

Any suggestions?

---

### Post by ajgreeny on 2009-08-27
You probably simply need to change the *System > Preferences > Preferred Applications* settings to Custom, with the command *firefox-3.5*

---

### Post by dragos240 on 2009-08-27
Probably not, try this:
sudo apt-get remove firefox && sudo apt-get install firefox.

---

### Post by rcbinwi on 2009-08-27
I'll give it a shot and let you know the results.

---

### Post by rcbinwi on 2009-08-27
PROBLEM SOLVED

I uninstalled and reinstalled Firefox, to be safe.  I noticed that my preferred setting was already on "Custom."  When I switched it to "Firefox" it worked like before.

Thank you for your help.

---

