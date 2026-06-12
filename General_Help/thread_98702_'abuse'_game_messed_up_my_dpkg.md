---
title: "'abuse' game messed up my dpkg"
date: 2005-12-03
forum: General Help
---

### Post by AmphetaMarinE on 2005-12-03
First up, hello all... what a wonderful community.
As my first post, I thought I should mention that...

Anyway, on to the meat in this sandwich...

After installing the small side-scroller game 'abuse' I found my automatic updates had stopped working.
It took a few days to rear it's head, as when I performed the install in the first place, no updates were available...

Well... when I tried to do an auto-update, I would receive an error that it had failed, and to check the terminal window to see what was going on...
Terminal window was (of course) empty...

So I tried an apt-get dist-update, and was met with the following errors...
```
Sub-process /usr/bin/dpkg returned an error code (2)
invalid	package name character not allowed only	letters	digits and _ allowed
```

Same errors when i tried an 'apt-get remove abuse'

After a bit of toiling.. I found the problem, so if anyone else experiences this, hopefully I will be of some help...

It seems that 'abuse-frabs' (Extra levels for abuse etc...) modified my '/var/lib/dpkg/status' file incorrectly...

In the priority section of the entry for abuse, it was listed as 'optionalCategory: game'

I think the problem was the colon, as when I modified it to say only 'optional', all worked correctly again....
I then removed abuse correctly, as I am not sure I want anything that will possibly stop my updates working... being that i am only about a 2-week old linux user, I will surely forget the fix, and have to go through all my trouble again ;)

Also, could anyone point me in the right direction as to where to report this as a bug to the author of the game?

Cheers all,
AmphetaMarinE

---

