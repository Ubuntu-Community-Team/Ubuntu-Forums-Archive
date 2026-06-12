---
title: "Ubuntu Crash"
date: 2008-10-19
forum: General Help
---

### Post by re2851 on 2008-10-19
I wasn't sure where to put this and seemed like a good place.

I have ubuntu and it was working great, i just got dual monitors setup and running correctly and everything was fine for like 3 days. then about 2 hours ago i tried to change the desktop background, it changed.  then i clicked on the desktop and it went to a black screen with white wording on it.

*Starting anac(h)ronistic cron anacron      [OK]
*Starting deferred execution scheduler atd  [OK]
*starting periodic command scheduler crond  [Ok]
*Checking battery state...                  [OK]
*Running local boot scripts (/etc/rc.local) [Ok]

After this comes up it just stays there and doesn't go away.  I read a similar post about someone with this problem and some said to press Alt+F7 and AltF8.  I tried that and pressing the first just takes me to a black screen with a blinking underscore, but i can't type anything, and the latter takes me back to the screen with the writing.  It only happens when I click on my desktop background and it didn't start happening until i changed my desktop background.  So what is this screen? and how can i get back to my desktop if it does happen or stop it from happening at all

Any ideas?

Thanks

---

### Post by forger on 2008-10-19
Which Ubuntu release?

Create a new user from system > administration > Users and groups > "Unlock" and "Add user". Log in from there and try it on that user, does the same thing happen? If it does, file a bug a bug report: [https://bugs.launchpad.net/ubuntu/+filebug](https://bugs.launchpad.net/ubuntu/+filebug)

---

### Post by Tux+ on 2008-10-19
Sounds like it's dropping to the terminal for some reason. Try pressing ctrl+alt+F8

---

### Post by re2851 on 2008-10-19
ok, so, i tried to create a new user, and no i didn't do it on the new user.  i switched back to my main username and it did it again, i tried the ctrl+alt combination, nothing happened. thanks for trying though, but any other ideas, it's super annoying that i can't click on my desktop or i have to restart the computer.

---

