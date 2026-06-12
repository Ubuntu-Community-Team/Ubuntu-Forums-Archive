---
title: "Can't seem to get fglrx to run instead of mesa"
date: 2008-05-04
forum: Hardware
---

### Post by missingno on 2008-05-04
No matter what I do, fglrxinfo keeps saying that mesa is being used rather than fglrx. I've set xorg.conf to use fglrx as the graphics driver, and yet it keeps saying that it's using mesa instead. I've looked this up on the wiki and tried several solutions listed there, and nothing has helped.

---

### Post by missingno on 2008-05-05
Also, I'm not sure if this is related, but I've never had this issue in 7.10 and I'm assuming this is happening due to the wrong driver running. Every time I resume from suspend, hibernate, or simply a screensaver, my display starts going screwy:
[[IMG]http://img376.imageshack.us/img376/4827/screenshot12ee7.th.png[/IMG]](http://img376.imageshack.us/img376/4827/screenshot12ee7.png)

I've tried completely removing and reinstalling xscreensaver, but it didn't help. How do I fix this?

---

### Post by missingno on 2008-05-07
Well I've been able to solve the screensaver issue by simply turning off screensavers, though I'd prefer a way of actually fixing these issues. Is anyone able to help?

Oh, and for reference, I forgot to mention that my graphics card is a Radeon x1200.

---

### Post by jaxpiron on 2008-05-08
just upgraded last night from 7.10 to 8.04.

Got the same problem. After upgrade fglrxinfo says "mesa" though xorg.conf and the conf files look alright.

By the way, I have *always* ran into this same problem at each upgrade (6.10 -> 7.04, 7.04 -> 7.10, and now 7.10 -> 8.04) and got things working only after a clean install. Can't figure out whats going on, any help to understand would be appreciated (kinda boring having to burn a cd for each new version and install it).

My system is a Dell inspiron 9400, with the ati x1400 graphic card.

This last time I have also tried to run envyng (never used it in the past) and it said "Success!" but unfortunely the graphics still don't work and fglrxinfo keeps saying "mesa". :(

Any clue, anyone?

---

### Post by jaxpiron on 2008-05-09
Update:

Alright I got it perfectly working after a fresh install.
Looks like something goes wrong if upgrading.

Did this:
Clean install.
Enable restricted drivers.
Downloaded latest Ati driver.
Change permissions to make it executable.
Run it (be aware that it happens to fail whenever u keep it on a fat32 partition with [signal caught, extraction failed] error... just move it on an Ext partition and run it to solve this problem.) and follow the installer.
Set visual effects to extra.
Install compiz and have fun :)

---

