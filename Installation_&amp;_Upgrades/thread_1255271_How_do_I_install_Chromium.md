---
title: "How do I install Chromium?"
date: 2009-09-01
forum: Installation &amp; Upgrades
---

### Post by mbuehl on 2009-09-01
been looking for almost an hour! no luck.

can anyone advise me on where to look?

edit: apt-get install chromium worked.

/bonkself

double edit: LOL this is just a game! hahahhahahaha, problem still persists :P

---

### Post by colau on 2009-09-01
> **mbuehl said:**
> been looking for almost an hour! no luck.

can anyone advise me on where to look?

edit: apt-get install chromium worked.

/bonkself

double edit: LOL this is just a game! hahahhahahaha, problem still persists :P
Hello,
Does this help?
[chromium]("http://www.sucka.net/2009/08/install-the-chromium-browser-in-ubuntu-9-04/comment-page-1/")

---

### Post by jacksaff on 2009-09-01
I assume you mean the google browser?

First result for googling "chromium unbuntu" was this:

[http://www.stefanoforenza.com/chromium-on-ubuntu-how-to/]("http://www.stefanoforenza.com/chromium-on-ubuntu-how-to/")

---

### Post by colau on 2009-09-01
> **mbuehl said:**
> been looking for almost an hour! no luck.

can anyone advise me on where to look?

edit: apt-get install chromium worked.

/bonkself

double edit: LOL this is just a game! hahahhahahaha, problem still persists :P
Do you use ubuntu 9.04 or ubuntu 8.10?

---

### Post by mbuehl on 2009-09-01
> **colau said:**
> do you use ubuntu 9.04 or ubuntu 8.10?

9.04

---

### Post by colau on 2009-09-01
> **mbuehl said:**
> 9.04
Have you installed Chromium?

---

### Post by ubulette on 2009-09-01
> **jacksaff said:**
> I assume you mean the google browser?

First result for googling "chromium unbuntu" was this:

[http://www.stefanoforenza.com/chromium-on-ubuntu-how-to/]("http://www.stefanoforenza.com/chromium-on-ubuntu-how-to/")

Most of the instructions found in blogs are months old and are either wrong, or obsolete.
The only maintained instructions are in the PPA board: [https://launchpad.net/~chromium-daily/+archive/ppa](https://launchpad.net/~chromium-daily/+archive/ppa)

---

### Post by CrusaderAD on 2009-09-01
I got it working with crossover, but it wasn't that impressive.

---

### Post by gradinaruvasile on 2009-09-01
Or just run this script i attached. It fetches the latest buildbot build from chromium dev site, unzip it in your home folder (/home/your_user_name/chrome-linux), makes a menu link under applications->internet. 

Does not work with 9.10 (karmic) due to compilation issues i think. The script has to be launched from a terminal, press any key when asked or ctrl-c to abort installation. 

Do not launch the script when u have no internet connection cause it will just erase the installed version of chromium (my fault being lazy...). Anyway if u have ur connection back it will install it back nonetheless...

---

### Post by ubulette on 2009-09-01
> **raptormanad said:**
> I got it working with crossover, but it wasn't that impressive.

crossover? :-k why run a wrapped Windows binary when we have native ubuntu builds for all distributions from hardy to karmic, with tight integration in the desktop?

---

### Post by ubulette on 2009-09-01
> **gradinaruvasile said:**
> Or just run this script i attached. It fetches the latest buildbot build from chromium dev site, unzip it in your home folder (/home/your_user_name/chrome-linux), makes a menu link under applications->internet. 


same as with crossover, why is that needed?

There's the PPA if you want native builds of the Open Source Chromium, and Google also provides debs in their -dev channel if you prefer Google Chrome binaries.

---

