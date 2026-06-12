---
title: "Strange System Updating Problems"
date: 2006-01-27
forum: Installation &amp; Upgrades
---

### Post by jss167 on 2006-01-27
I have the AMD64 bit Ubuntu Breezy version installed, but am having trouble with updating.  This is weird.

A short while ago, I noticed the first issue.  After a daily package update, my screen at the beginning when Ubuntu is loading and configuring(I think it's a splash?) changed from Ubuntu to Kubuntu.  All else worked OK.  Everything else says Ubuntu still.

About three days ago, I updated my system again and was told there were problems with documentation packages, which could not install.  Specifically Ubuntu docs and Kubuntu docs.  It also mentioned Edubuntu.  I use Ubuntu only, so this made no sense.  Synaptic called this a conflict and the terminal said so, too.  

I pulled up Ubuntu-docs and this is what it said:

depends: scrollkeeper
recommends: yelp
conflicts: ubuntu quickguide
conflicts: ubuntu faqguide
conflicts: kubuntu docs(<5.10-0.6.1)
conflicts: edubuntu artwork(<0.1.0-9.1)
replaces ubuntu faqguide

For Kubuntu docs:

depends: khelpcenter
conflicts: ubuntu docs
conflicts: edubuntu artwork

Everything else appears to update fine, if I deselect these two items(Ubunut docs and Kubuntu docs.)  I really would like to know why all this stuff is installed if I only use Ubuntu, what the problem is, and how to fix it.  Thanks.

---

### Post by stalefries on 2006-01-27
um, I would try removing only Kubuntu docs. then see what other problems are left.

---

