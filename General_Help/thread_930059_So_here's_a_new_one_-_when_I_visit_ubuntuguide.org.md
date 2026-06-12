---
title: "So here's a new one - when I visit ubuntuguide.org my computer logs me out."
date: 2008-09-25
forum: General Help
---

### Post by ticopelp on 2008-09-25
As in, logs me out of my session, as in I go back to the login screen. This has happened three times in a row, and just with the Ubuntuguide page for Gutsy (my current distro). 

The only unusual thing is, I'm running Firefox 3, which I upgraded to manually following instructions I found here on the forums. But I would think that if there was a problem, it would just crash Firefox, not bump me out of my desktop session!

Any ideas on why this might be happening?

ETA: I already tried clearing all my cookies, session data, etc. No dice there. I also thought it might be a weird Compiz problem, but it does the same thing running in metacity.

---

### Post by Monotoko on 2008-09-25
Well, thats definatly a new one....i would set up another account, and try it on there, if it doesnt work, try installing another browser, see if it produces the same results.

---

### Post by mbeach on 2008-09-25
first thing that comes to mind is to disable javascript and java (edit-preferences-content), then navigating to that page - just to rule it out (or in) as a place to start looking.  Certainly is strange behaviour.

---

### Post by mbeach on 2008-09-25
and just a follow-up - does this only seem to happen on ubuntuguide?  does it happen consistently or only once in awhile?

---

### Post by ticopelp on 2008-09-25
> **mbeach said:**
> and just a follow-up - does this only seem to happen on ubuntuguide?  does it happen consistently or only once in awhile?

It happens 100% of the time when I go to the Gutsy page for Ubuntuguide. (Not, interestingly enough, the front page for Hardy). 

I tried disabling Javascript and that still crashed my system. I'm going to try installing Opera and maybe rolling back to Firefox 2, although it's annoying to have to do that.

---

### Post by ticopelp on 2008-09-25
OK, I installed Opera and [http://ubuntuguide.org/wiki/Ubuntu:Gutsy](http://ubuntuguide.org/wiki/Ubuntu:Gutsy) doesn't crash there... so it's definitely a Firefox issue.

But how do I fix it?!

---

### Post by Monotoko on 2008-09-26
Search for firefox in the add/remove

Remove it from your system, dont worry about the warning that ubuntu-desktop will be uninstalled

now try to reinstall firefox and see what happens

---

### Post by mbeach on 2008-09-26
good question.  I've recently just put Hardy on laptop which has been going fairly smoothly, however, firefox is exhibiting some strange behaviour crashing occasionally but usually due to some flash on the page.  I've been also getting some complete desktop failures where the keyboard becomes unresponsive and the caps lock light begins to flash, trackpad ceases to function.  I'm thinking that it may have nothing to do with firefox.  I've just downloaded Opera to see if I see the same behaviour - in the meantime, I plan on looking into these other issues (I'm suspecting the wireless card as the root of all evil).  This is the first laptop I've really tried Ubuntu on - have never had stability issues on desktops and servers.  

So back to your question - I was told to look in /var/crash for details, but so far nothing has appeared there.  Also told to run dmesg to see if that yields any good stuff just after a program crash, however, I thought that was for boot up issues.

I've never seen something kick you out to the log in screen before.  That is still very interesting.

[edit]
just noticed an update to firefox 3.0.3 available - perhaps it make your problem go away?

---

### Post by Sycron on 2008-09-26
It very strang that I never had problems with firefox.

---

