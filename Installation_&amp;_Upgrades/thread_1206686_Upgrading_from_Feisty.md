---
title: "Upgrading from Feisty"
date: 2009-07-07
forum: Installation &amp; Upgrades
---

### Post by dwight on 2009-07-07
My parents have a Kubuntu Feisty box which I installed ca 2 years ago. They were happy with it and everything was working fine so I didn't see much point in upgrading it. Now recently they tried to install some programs and turned out that the repo no longer has Feisty packages. I'm under the impression that it's only safe to upgrade one version at a time, so directly upgrading to Jaunty would not be 'safe'. However, Gutsy packages are off the repos too now so they can't start the step-by-step upgrade either (Feisty -> Gutsy -> Hardy -> Intrepid -> Jaunty). Is there a way to resolve this? What makes things more complicated is that I'm in another country for 2 months so I cannot directly do it myself. I don't want to take the risk of having them try to do a clean install cause that might leave them without a working computer, plus they don't know how to backup existing data. So the ideal solution is that I send them some script which they run with sudo. How risky would it be if I just sed their sources.list file and replace feisty with jaunty and make them do a dist-upgrade?

---

### Post by Idefix82 on 2009-07-07
Why can't you write a script for them that will back up their data? After that a fresh install on a basic non-dual boot system is pretty easy, is it not?

---

### Post by dwight on 2009-07-07
Thanks :) Not a bad idea. But unfortunately they can't burn CD's as they have a read-only drive. So I need to do this with the system they have. Or should I just tell them to wait till I get back? Basically my dad wants to install some programming language to try it out a bit, but it's nothing crucial. The system works fine otherwise, they can do their browsing and emailing just fine. So if upgrading from Feisty involves a significant risk of ending up with a non-functional machine I'd rather postpone it.

---

### Post by oldos2er on 2009-07-07
You can try this for Feisty: [http://old-releases.ubuntu.com/releases/7.04/](http://old-releases.ubuntu.com/releases/7.04/)

---

### Post by dwight on 2009-07-07
Not quite sure how these images would help me... I don't want to install Feisty. I either need a feisty repo somewhere or a way to upgrade from feisty without having to backup data and burn a new cd.

---

