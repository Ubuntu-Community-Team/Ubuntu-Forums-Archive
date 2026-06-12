---
title: "Question about where files are installed"
date: 2008-12-03
forum: Installation &amp; Upgrades
---

### Post by Rocket Sock on 2008-12-03
I've asked this three different times now, hoping someone can help me. 

I've got a 10gb / partition, and a 90GB /home partition. My question, is what partition are programs installed after using a package manager to get them. If it's /, how do I change it to be installed on /home instead, considering I'd rather not run out of space.
And how do I figure this stuff out anyway? 

Also, what does the package manager do when it downloads/installs? Does it get rid of all the files it uses to install the program? Or just leave it there for me to delete?

Sorry for the basic questions. As you can tell, Im still brand new to everything.

---

### Post by cariboo on 2008-12-03
All files get installed somewhere in / depending on what type of file it is. Downloaded packages are archived in /var/cache/apt/archives, once they are installed there is really no need to archive the packages. The way to remove them is to open a Applications-->Accessories-->Terminal and type:

```
sudo apt-get clean
```

and to get rid of uneeded dependencies, in the same terminal type:

```
sudo apt-get autoremove
```

Jim

---

### Post by Rocket Sock on 2008-12-03
Thanks for the help. 
So Im kinda confused here though. Everyone recommends that you use 10 gigs for root, and just throw a **** ton into /home. 

But I plan on installing a fair number of programs, not to mention the games I'll install with Wine. Is there a way to install them to /home; SHOULD I install them to home? Please, any help, recommendations would be appreciated.

---

