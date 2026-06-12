---
title: "Why I cannot keep KK"
date: 2009-11-05
forum: Installation &amp; Upgrades
---

### Post by realn on 2009-11-05
I performed a fresh install of KK as instructed in this post
[http://ubuntuforums.org/showthread.php?t=1310303](http://ubuntuforums.org/showthread.php?t=1310303)
I wanted the latest KK features but with KDE 3.5.

 I did that, one of the first packages I want to install is KIMA - a kicker monitoring applet. 
 Problem: IT IS MISSING from the repositories. I did a search - apparently it's missing starting from 8.10
 Please , could someone help me by telling me:
- is there any repository I should find my favourite app - Kima, or do I need it to download the hardy version and install it by hand;
- are there many application which were available on Hardy and missing starting from 8.10.

If it turns out that there are applications missing - I will gladly and f...ing angrily fall back to Hardy. What is the use of having a new distribution, if there are lots of useful and stable pieces of software missing from it? I don't understand - are we at a fashion show or are we in the practical computer world (or maybe they are more or less the same concept - I want the latest thing, beacuse it's the latest, no matter if it's the ugliest, clumsiest piece of crap).
 Please help me, I am again frustrated at max by Ubuntu's_sometimes_unbearable_pain_in_the_***_release_policy).

---

### Post by realn on 2009-11-05
I've been trying to install Kima from hardy repository - it seems that its dependencies are KDE4, and not KDE3
kima:
 Depends: kdelibs4c2a but it is not going to be installed

---

### Post by madscientist159 on 2009-11-05
I will repackage kima for KDE3 ASAP.  Every now and then an older KDE3 app is retained in the Universe repository and has also slipped through the cracks on my end as far as repackaging is concerned.

Repackaging is required for two reasons:
1. The KDE3 file structure resides in /opt/kde3, not  in /usr like the Universe packages assume
2. Those same packages have a tendency to be removed once they are discovered by the Kubuntu maintainers.  Rebuilding them in my PPA preserves them permanently with a -kde3 suffix.

Thank you for bringing this to my attention!

Timothy Pearson
KDE3.5 Developer/Maintainer

---

### Post by realn on 2009-11-08
Thank you, Tim, I was decided to dump KK only for this relatively minor issue. I can carry on with KK, thanks to you.

---

### Post by realn on 2009-11-23
Hi, I found another package missed in KK+KDE3 - gdebi-kde.
I would like to change the thread title to smth like: missing packages from KK+KDE3, or smth like this, but I don't know how to do it.
Problem reported via pm to Tim.

 Thank you all.

---

### Post by realn on 2010-07-20
Solved - fallback to Kubuntu Hardy Heron waiting for a real LTS release.

---

