---
title: "upgrade to ubuntu 9.04 in Dell Latitude D630 - success!"
date: 2009-05-14
forum: Installation &amp; Upgrades
---

### Post by **martha** on 2009-05-14
Just to inform that the upgrade worked fine for me. I have a Dell Latitude D630, with Nvidia graphics card.

I had some problems with 'partial upgrade' messages popping up, but the solution was simple:

In a terminal, I did

sudo apt-get update
sudo apt-get dist-upgrade

After this, I still had 'acroread' as a package that couldn't be upgraded. So I removed it with

sudo apt-get purge acroread

Then I restarted the upgrade in the usual way and everything is now working fine. 

The connection to the projector/beamer was a problem in the previous version. I had to turn off compiz every time I had to make a presentation. I didn't test that yet with Jaunty. As soon as I do so, I will post an update here.

Cheers

---

