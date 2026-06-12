---
title: "karmic empathy won't import pidgin contacts"
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by sloggerkhan on 2009-10-31
Every time I launch empathy it offers to import my pidgin contacts, I hit yes or whatnot, and then empathy opens and my contacts have not been imported.

Needless to say I am continuing to use pidgin in the meantime, but it would like to know if there's a fix so I can give empathy a try.

---

### Post by pablo180 on 2009-11-02
I'm getting the same issue since Karmic. I had used Empathy before, but now I just get the same screen every time I use it. I am also just sticking with Pidgin till this is fixed.

---

### Post by h6w on 2009-11-04
I've reported a bug about this:
[https://bugs.launchpad.net/ubuntu/+source/empathy/+bug/474929](https://bugs.launchpad.net/ubuntu/+source/empathy/+bug/474929)

It seems, however, that this is caused by IRC accounts stopping the import process:
[https://bugs.launchpad.net/bugs/388906](https://bugs.launchpad.net/bugs/388906)

---

### Post by firfin on 2009-11-17
I Just tried to import without importing my irc accounts (unchecked the IRC accounts) Still no contacts get imported.

---

### Post by wobb on 2009-11-17
> **sloggerkhan said:**
> Every time I launch empathy it offers to import my pidgin contacts, I hit yes or whatnot, and then empathy opens and my contacts have not been imported.

Needless to say I am continuing to use pidgin in the meantime, but it would like to know if there's a fix so I can give empathy a try.

Same here too. I have switched to aMSN.
Cheers,

---

### Post by firfin on 2009-11-17
I'm sorry for the misinformation. Unchecking IRC contacts DID work for importing the rest of the accounts. It just took a while for the contacts list to fill (next reboot they were there.)

BTW it helps to have telepathy-idle installed (by default for me (karmic upgrade from jaunty), but that's what I gathered from bug reports)

---

### Post by MikeFlint on 2010-02-12
I was having the same problem ... launch Empathy ... offer Pidgin account import, accept, nothing happens.


I tried this about 4 times.

Having checked I have all the dependencies in synaptic (I did), I tried Empathy from a terminal to see if I was getting any errors.  After a long delay (about 20 seconds), I was eventually shown my account with a tick-box to make it active, and then it seemed to work.

Quite why it failed to start with is a mystery.  I'll keep Pidgin around in case.

---

