---
title: "Ubuntu 9.04 to 9.10 Upgrade?"
date: 2009-10-19
forum: Installation &amp; Upgrades
---

### Post by chrispche on 2009-10-19
How does upgrades go as far as stability is concerned? If I install 9.04 will an upgrade to 9.10 in 10 days or so time be OK? I currently run Fedora 11, I miss Ubuntu and want to return. Is it worth installing 9.04 or should I wait for 9.10.

I have to admit to installing 9.10 beta, but, it was very unstable so I went back to Fedora 11.

---

### Post by chrispche on 2009-10-19
Actually thinking about it 9.04 uses ext3 doesn't it? And 9.10 ext4 so how does that work when upgrading?

---

### Post by dhavalbbhatt on 2009-10-19
Anytime, a fresh install is better than an upgrade, especially as it relates to 9.10, given that there are some significant changes to 9.10.

> **chrispche said:**
> Actually thinking about it 9.04 uses ext3 doesn't it? And 9.10 ext4 so how does that work when upgrading?

With regards to the above question, if you were to "upgrade" from 9.04 to 9.10, your current filesystem (ext3, provided you are using Ubuntu 9.04 or less) **_won't_** be upgraded to ext4 filesystem. For that you will have to perform a "fresh install".

---

### Post by chrispche on 2009-10-19
I think, what I'll do is continue to use Fedora 11 and wait till Ubuntu 9.10 is out then do a fresh system install. Hopefully the bugs will be all ironed out in 10 days time.

---

### Post by driven1 on 2009-10-19
Related question. If I do a fresh install, is there any way to avoid going back and manually reinstalling all of the medibuntu packages, and additional apps that I have? That is the biggest advantage of doing the upgrade IMHO.

---

### Post by jscudder on 2009-10-19
If I upgrade from 9.04 to the beta 9.10 today, will the beta 9.10 be automatically upgraded to the final release after next week?  Or will I have to reinstall 9.10?

John

---

### Post by bulldog on 2009-10-19
Some years ago I found this,don't know from who it was,but anyway,I did not try it myself,so I do not know of it still works,your question about this did me do a search for it.

dpkg --get-selections > mypackages 

#writes all installed packages to "mypackages"

# save "mypackages" on a USB stick, copy it to a fresh install

cat mypackages | sudo dpkg --set-selections 

#selects all packages from "mypackages"

sudo apt-get dselect-upgrade #installs them

---

### Post by driven1 on 2009-10-19
> **bulldog said:**
> Some years ago I found this,don't know from who it was,but anyway,I did not try it myself,so I do not know of it still works,your question about this did me do a search for it.

dpkg --get-selections > mypackages 

#writes all installed packages to "mypackages"

# save "mypackages" on a USB stick, copy it to a fresh install

cat mypackages | sudo dpkg --set-selections 

#selects all packages from "mypackages"

sudo apt-get dselect-upgrade #installs them

Thanks, I may give it a try.

---

### Post by dhavalbbhatt on 2009-10-19
> **jscudder said:**
> If I upgrade from 9.04 to the beta 9.10 today, will the beta 9.10 be automatically upgraded to the final release after next week?  Or will I have to reinstall 9.10?

John

You don't need to re-install 9.10 after RC is released. All you have to do is ensure the package is upgraded to the latest release. You can find a whole host of posts on how to do that - just do a search.

---

### Post by vrkalak on 2009-10-19
I would recommend a fresh install of Ubuntu Karmic 9.10.

I have been updating/upgrading my Ubuntu Jaunty 9.04 _daily_, since Alpha 2. As a 'testing' Ubuntu distro.
Many of the upgrades are considerible in size, from Alpha 6 to Beta ... I had almost 300 upgrades.  Some Daily Builds are almost 175 updates/upgrades of various files, libs and Apps.

To upgrade from a stock 9.04 to 9.10 would be emmense and would take hours, if not days, to download.  At this point, it would be better to just wait for the Final Release of Karmic 9.10, then download an ISO file and do a fresh install.  Of course, make sure you back-up all your data or save it to a '/home' partition.   I, also, have a partition with Xubuntu on it, that I am waiting to upgrade (actually, a fresh install)

But, I can tell you ... it will be worth it.  The new Karmic Koala rocks!!  :guitar:

---

