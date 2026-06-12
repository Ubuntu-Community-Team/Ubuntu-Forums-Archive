---
title: "Remove and reinstall broken packages without deinstalling many others?"
date: 2006-02-10
forum: Installation &amp; Upgrades
---

### Post by adelaar on 2006-02-10
Hi,

I have a recent installation of kubuntu 5.10 and added many packages.

I would like to install programs that require kdelibs4-dev, but the installation with
> 
sudo apt-get install kdelibs4-dev

fails, because apt-get afterwards subsequently tells me there are the following dependences (>> means "depends on"):
> kdelibs4-dev >>libarts1-dev (>= 1.4.0) >> libartsc0-dev, libarts1c2
and
> libartsc0-dev >> libartsc0
(Sorry for no exact quotes; I have a German version of kubuntu installed and apt-get's messages in German wouldn't be very useful for most of you)

So in the end I would need libartsc0 and libarts1c2. However, these packages are installed, but obviously too new:
- it wants libartsc0 1.4.3-0ubuntu1, and I have 1.5.0-0ubuntu0breezy1
- it wants libarts1c2 1.4.3-0ubuntu1, and I have 1.5.0-0ubuntu0breezy1

When I tried to deinstall them, apt-get warns me that this would remove a load of other crucial packs, which I definitely wouldn't want. Also, apt-get sends an error message which would be something like "E: broken packages" in English.

So does anybody have an idea what is going on here and what to do here? How would I remove and reinstall these packs without breaking my system?
Please help, any advice really welcome - thanks!

---

### Post by adelaar on 2006-02-10
Can really no one help me with this? I tried a lot of things like
> apt-get --reinstall install ...
and many others...
aRts Sound system doesn't seem to work.

Searching the web didn't help either...

---

### Post by percival95 on 2006-02-10
After the initial install of kdelibs4-dev fails try
sudo apt-get -f install
sometimes this will help

---

### Post by adelaar on 2006-02-10
Thanks for trying, but - no, didn't help...

Is there any way to (temporarily) get rid of a package without deinstalling other packs that depand on it?

---

### Post by CookieOrc on 2006-02-10
I do not think that hould be possible. Due to the depencencies. You can try installing over them... but you would have to download the packages manually

---

### Post by adelaar on 2006-02-10
Yes, that did the job! Turned out to be surprisingly easy... :-D 
Thanks a lot for the tip!
adelaar

---

