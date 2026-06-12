---
title: "Ubuntu will not start"
date: 2009-08-12
forum: Installation &amp; Upgrades
---

### Post by mcoletta on 2009-08-12
I have installed the latest version of Ubuntu as a duel boot on my 64bit Vista desktop. installed into a seporate drive w/120GB free space. first couple of launches were fine. then I updated some of the applications and installed others that were on the apps list and now when launched, all I get is a black screen. I went through the recovery steps and tried everything but the command line. I had no idea what to type as this was my first day with linux.

Really need some assistance.
Thanks in advance:(

---

### Post by mikewhatever on 2009-08-13
Try the following two commands:

aptitude install ubuntu-desktop

sudo dpkg-reconfigure -phigh xserver-xorg

The first one will make sure all the default packages are in place, and the second will try to reconfigure the graphical backend.

---

