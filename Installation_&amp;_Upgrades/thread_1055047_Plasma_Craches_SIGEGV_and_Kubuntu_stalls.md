---
title: "Plasma Craches SIGEGV and Kubuntu stalls"
date: 2009-01-30
forum: Installation &amp; Upgrades
---

### Post by nettobr on 2009-01-30
Hi People,

I´m having a plasma crash problem, the screen gets blank and nothing more happens...

This began (I Think) after a full Kubuntu Update I have ordered last night. and after that I can´t login my Dell Latitude 131l NoteBook.  I´m using Kubuntu 8.10.

I tried to boot recovery mode option, to fix FS, fix packages, etc.. but no way to make Kubuntu work.

All I have to do is a HALT, pressing Power Bottom.

I´m getting PLASMA SIGEGV error.

Hope Kubuntu crew has a patch for this problem.

Best Regards,

NettoBr

---

### Post by dabl on 2009-01-30
Yep, that happened to me, too.  Lacking any better idea, I booted into text mode, renamed the hidden ~/.kde directory, and rebooted.  The good news is, it works.  The bad news is, all your settings have to be redone.

---

### Post by nettobr on 2009-01-30
Hi, Dabl,

As an old boss of mine was used to say, for each problem we have at least 5 solutions...

Well, i took a diferent way: entered recovery mode as root and made a dpkg remove of plasmoid.

But I´ll wait for the solution of plamoid, cause I like it.

Thanks a lot,

---

