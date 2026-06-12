---
title: "Do you recommend backports?"
date: 2009-10-28
forum: Installation &amp; Upgrades
---

### Post by Nopposan on 2009-10-28
How satisfied are you with backport updates?  Should I enable it for new users?

I'm installing Xubuntu 9.04 (or maybe 9.10) for people who've never used Linux before; O.K., I've already made this decision so don't try to talk me out of it.

What I want to know is whether to enable updates from backports.  Here's why I ask.  I don't want to bother the new user with upgrading or reinstalling their OS every six months, but I do want to provide them with up-to-date software.  I've configured the update manager to only notify of upgrades to new "long-term support" releases, and I'm planning to enable backports . . . but I'm posting this poll to see if folks who've tried this method have been satisfied.

---

### Post by p2bc on 2009-10-28
First o all I don't see why anyone would talk you out of anything.

If you want to "install it, and forget it" stick with 04 version, i.e. 9.04 since they are the one that are LTS (Long Term Support)

As for keeping things up to date, the software won't install or update anything that is not already installed. For instance Firefox 3.0 and 3.5. If you have 3.0 installed it will keep upgrading, as long as there are some 3.0.1 -> 3.0.2 -> 3.0.3. It won't install Firefox 3.5 unless you tell it to, because it see it as two different application. Same goes for OpenOffice 2 or 3, or Python 2 or 3, and so on. So what ever applications you have installed when you "hand over" the computer will be the ones that are updated. With that said you also have to make sure the sources are enabled for those application in your sources.list file.  But if you have ever sources enabled it would not harm the application already intalled or being up dated.

---

### Post by ajgreeny on 2009-10-28
> **p2bc said:**
> If you want to "install it, and forget it" stick with 04 version, i.e. 9.04 since they are the one that are LTS (Long Term Support)
9.04 is not a LTS version, that was 8.04.  The next LTS will be 10.04 I think, next April.

---

### Post by louieb on 2009-10-28
Running Hardy on my desktop. Even with the backports repositories turned on don't get a lot of updated applications. Example Firefox 2 - Firefox 3 update came from main. Open Office 2.4 to OO 3.1 not in backports.  Had to Download it from the OO site. Pidgen not in backports - had to add a PPA repository. 

Don't see having backports enabled is going to make much difference.

---

### Post by en soph on 2009-10-28
on ubuntu 8.10 (I think), backports broke my system several times (e.g. sound disappearing, kernel not booting, etc.) until I realized it was them. with a clean install and disabling the backports it worked like a charm. I do NOT recommend them if you're not a developer and also the developers should make it harder to enable them (maybe deleting the option from software sources and making them accessible only through editing sources.list) since they are really dangerous (you know... it's mostly untested software after all).

the proposed repositories are ok, though.

as for your problem, I'd enable not-LTS distribution upgrades, since it's a relatively clean and quick process after all, and it keeps the software updated to the latest stable versions -- backports does not upgrade to the new major releases (see the posts above mine).

---

