---
title: "ubuntu falters on apt-get update, upgrades in general"
date: 2009-07-08
forum: Installation &amp; Upgrades
---

### Post by pythonscript on 2009-07-08
I'm posting this here even though it involves a virtual machine, since I think the problem is more related to the system itself and not the vm. I installed ubuntu 9.04 without a desktop environment (not the server edition, I just used the alternate install CD) but it keeps freezing up during updates/upgrades. Sometimes, I run sudo apt-get update, and it just pauses at a (seemingly) random percentage, at a whole assortment of repository updates. It's different every time. I tried it a couple of times, and it finally worked without my changing anything, but it freezes on some of the upgrades. Most recently, it gets up 6% of the upgrade download, perl-modules I think, and it just freezes. Any ideas? This is really frustrating that I can't update my VM at all. Should I just try re-installing it and see if that does anything? Thanks!

EDIT: Fascinating... After running through this about 20 times, I've noticed that it always hangs on the perl-modules when downloading the updates (it finishes updating the package list, after a few brief hangs throughout the update). Also, I'm pretty sure that the network is working; I've installed this exact same configuration in multiple VM's on this host computer, and they've all worked fine in the past (I don't have any others installed at the moment, so I can't field this one's performance against any others). If you need any more information, let me know. Thanks!

---

### Post by Soul-Sing on 2009-07-09
could you post the exact errors messages?

---

### Post by lökring on 2009-07-09
I have the same issue. Freezes after a while at a random position.. No other clues to why though.

However, when i changed the download server it worked again. .se server does not respond

---

### Post by pythonscript on 2009-07-09
There is no error message. It just freezes when trying to download the perl modules. How would I go about changing the update server? Preferably without installing a graphical interface at all. Thanks!

---

### Post by pythonscript on 2009-09-06
I changed some of the download mirrors and that fixed the problem. It might have been a problem with the mirrors that day. I marked this thread as solved before I posted this, so I thought I'd post the solution for archival purposes.

---

