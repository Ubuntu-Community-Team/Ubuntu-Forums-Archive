---
title: "apt asking for cd?"
date: 2006-01-05
forum: Installation &amp; Upgrades
---

### Post by bananana on 2006-01-05
I'm trying to install rosegarden4, and I get this message from apt:

Media change: please insert the disc labeled
 'Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)'
in the drive '/cdrom/' and press enter

Why is this necessary?  I don't have the cd, and don't want to download it again.  What's on the CD that couldn't be put into the repository?

---

### Post by heimo on 2006-01-05
Open Synaptic Package Manager, select Settings->Repositories, select Settngs, check "Show disabled software sources", click [close]. Uncheck the CD, click OK - choose Reload. That should do it. :) If not, let us know.

---

### Post by kumakun on 2006-01-05
I ran into this problem last night, installing the MS true type fonts. I found that if you go into synaptec, or your sources.list file and remove the CD as a repo it'll get your program from the other repositories.

Hope that helps.

/K

---

