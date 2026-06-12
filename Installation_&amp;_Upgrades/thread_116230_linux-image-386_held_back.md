---
title: "linux-image-386 held back"
date: 2006-01-12
forum: Installation &amp; Upgrades
---

### Post by Tom Bentley on 2006-01-12
I installed breezy on server earlier this week. Following the initial install, I added universe (breezy and breezy-security) to my /etc/apt/source.list and installed some packages. Now aptitude is telling me that linux-image-386 and linux-restricted-modules-386 are held back.

I think the problem is that:
[LIST]
[*]linux-image-386 depends on linux-image-2.6.12-10-386
[*]linux-restricted-modules-386 depends on linux-restricted-modules-2.6.12-10-386
[/LIST]
and these are unresolved dependencies. 

As I understand it linux-image-386 always depends on the lastest kernel image, and similarly linux-restricted-modules-386 always depends on the lastest restricted modules.

I don't understand why these dependencies are broken though, nor what I can do to fix it.

Thanks!

Tom

---

### Post by MartinG on 2006-01-12
This *might* be due to a faulty installation of your extra packages. Try one of the following```
sudo dpkg --configure --pending
sudo apt-get install -f
```This should fix any broken dependencies.

---

### Post by Tom Bentley on 2006-01-12
OK, I tried those, and I've still got the problem.

I've posted my problem to the main Breezy forum, since I guess this isn't really an installation problem.

---

