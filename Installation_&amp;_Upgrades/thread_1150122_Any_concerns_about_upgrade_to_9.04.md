---
title: "Any concerns about upgrade to 9.04?"
date: 2009-05-05
forum: Installation &amp; Upgrades
---

### Post by Mechphisto on 2009-05-05
I'm currently running 8.10 and I was wondering if I can anticipate any significant issues running the upgrade to 9.04.

Will there be any post-upgrade reinstallations that are a certainty, or re-configurations of things? Anything known to break altogether?

Thanks for any advice!
Liam

---

### Post by gpmiii on 2009-05-05
Unless your ready to troubleshoot - wait on upgrade.

---

### Post by wpshooter on 2009-05-05
I would not upgrade, if at all possible I would do a clean installation from scratch.

---

### Post by Mark Phelps on 2009-05-05
> **Mechphisto said:**
> 
Will there be any post-upgrade reinstallations that are a certainty, or re-configurations of things? 

If you've customized any system files (menu.lst, xorg.conf, etc), you may need to save them first so you have the modified versions to use to update any that get replaced.

> Anything known to break altogether?
Yeah -- 9.04 dropped ATI driver support for lots of video cards.  Unless you have an "HD" ATI card, you will be forced to use the open source drive.  And, if you have the restricted driver installed now, you may not get a desktop after upgrade.

---

### Post by lswb on 2009-05-05
If your system has intel graphics you may be dissappointed. There are several forum threads if you want more details.

---

