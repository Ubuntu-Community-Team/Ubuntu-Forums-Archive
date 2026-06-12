---
title: "Radeon HD 7870: Taking screenshots, desktop recording"
date: 2013-09-09
forum: Hardware
---

### Post by ty4 on 2013-09-09
Hey everyone!  This is pretty much what I'm looking for, I can't take screenshots because of my drivers as it only gives me a black screen with just the cursor, which are the fglrx proprietary drivers.  Everyone says that this isn't fixable, this is important to the issue I'm having because I can't record my desktop either, I'm using SimpleScreenRecorder so I can stream to Twitch.TV.  I get the same result for my output when I record my desktop, that being black screen with only the cursor.

I'm basically looking for a driver that gives decent 3D performance that will also let me screen cast.  Or maybe even a workaround for fglrx users!  And while I'm here, I get black windows too, like the Steam window will be all black, no buttons showing, but they're clickable, as I had to learn to memorize where buttons are because of this.  Any help would be GREATLY appreciated!  :)

---

### Post by mörgæs on 2013-09-09
For which AMD card?

---

### Post by ty4 on 2013-09-09
Oh, sorry about that!  I'm using the Radeon HD 7870.  I tried disabling the proprietary drivers but my computer got the "Check Battery Status... [OK]" hang so I reinstalled the post-release updates drivers through the recovery terminal to fix it, I was using the experimental ones before.

P.S. I should probably mention that I'm using ElementaryOS Luna, based on Ubuntu 12.04.  This issue happens to all Ubuntu users apparently, according to my research.

---

### Post by sena-akada on 2013-09-09
I'm using a Radeon 6670 with the FGLRX stable driver installed through System Settings. Apart from issues with Steam, everything else works fine (including taking screenshots & desktop recording). Is the issue only with Elementary Luna?

---

### Post by ty4 on 2013-09-09
> **sena-akada said:**
> I'm using a Radeon 6670 with the FGLRX stable driver installed through System Settings. Apart from issues with Steam, everything else works fine (including taking screenshots & desktop recording). Is the issue only with Elementary Luna?

I'll take a look on Google again, but the most common answer I got was that it was a FGLRX bug.  I never took a screenshot when I was using 13.04 before trying eOS so I believed that it was simply an eOS issue until I googled it.  Maybe I can use a console command to capture a shot and show the output if it's not good.

EDIT: My apologies, this is, in fact, an ElementaryOS issue.  After a closer look while googling the issue, it seems that ElementaryOS' Window Manager, Gala, is the culprit.  Sorry for wasting a thread, I may have figured that one out on my own if I spent more time on it, I noticed the issue this morning and wasn't patient enough when I got home from work.

The only thing I could think of is getting rid of Gala and replacing it with Compiz.  Gala has a launchpad so I could just compile the source if I want it back.

EDIT2: Using Compiz fixed the issue!  All I had to do was install Compiz, then add 'compiz --replace' in startup applications.

---

### Post by mörgæs on 2013-09-10
Good, then please mark the thread 'solved'.

---

