---
title: "Help needed : restoring 9.04 from 9.10 bad install"
date: 2009-10-25
forum: Installation &amp; Upgrades
---

### Post by vur246 on 2009-10-25
First I admit my colossal blunder by trying to upgrade 9.04 to 9.10 beta yesterday, so I fully deserve the outcome - upgrading died on unpacking/installing libc, and now I can't boot ubuntu 9.4.

It turned out my back-up is corrupted, so I would like to ask for recommendations :

2. Is it possible somehow to continue install from the point it died (afraid not)?

1. Is it possible to "roll-back" somehow this half installation back to 9.4 ?

2. If not (I am afraid this will be the answer), what would be the most reasonable way to undid the damage ?
  
I can boot with knoppix, mount the home partition and copy /home to my network drive, then reinstall 9.4 or do fresh install of 9.10 next week, bring my /home back and reinstall all the packages.

Anything more sophisticated/less tedious ?

Thanks in advance

---

### Post by aheckler on 2009-10-25
Why not just boot into Knoppix, save your personal data to your network drive, then do a fresh reinstall of 9.04? That what I would do, just to be as safe as possible with my files.

---

### Post by Mark Phelps on 2009-10-25
> **vur246 said:**
> 2. Is it possible somehow to continue install from the point it died (afraid not)?
Answered your own question.

> 1. Is it possible to "roll-back" somehow this half installation back to 9.4 ? Nope.  No "System Restore" capability available by default.  Can only do this if you did a backup before the upgrade.

> 2. If not (I am afraid this will be the answer), what would be the most reasonable way to undid the damage ?
  
I can boot with knoppix, mount the home partition and copy /home to my network drive, then reinstall 9.4 or do fresh install of 9.10 next week, bring my /home back and reinstall all the packages.

Anything more sophisticated/less tedious ?
As already advised, the back off, reinstall is the best approach.

---

### Post by vur246 on 2009-10-25
Thanks for advises 

I knew there is no magic way to get back to 9.4 easy, but I still hoped for some hack/trick. Now need to do fresh install of 9.4.

---

