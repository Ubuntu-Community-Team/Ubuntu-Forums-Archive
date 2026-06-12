---
title: "Should I have a separate 'home' partition?"
date: 2009-03-06
forum: Installation &amp; Upgrades
---

### Post by Ascenti0n on 2009-03-06
Hi all,

I'm wondering if I should I have a separate 'home' partition? when installing Ubuntu?

What are the advantages? is it true if I have a home partition, that if I installed a fresh installation, I wouldn't have to install the apps again, ie kate, gvim, zimbra etc?

---

### Post by taurus on 2009-03-06
No.  The apps which are part of the system will be reinstalled but your personal files and settings will be saved or carried over if you ever reinstall or upgrade.

---

### Post by Ascenti0n on 2009-03-06
Thanks taurus. the reason I ask is that though I have an 8.10 dual booted machine with winXP, I see quite a few posts and blogs from people who are very apprehensive about upgrading their installation and would rather have a fresh install.

With 9.04 just around the corner, I was thinking if I have to do a fresh install, I would have to install the apps that I installed that were IN ADDITION to those installed by default.

Am I on the right track?

---

### Post by x33a on 2009-03-06
when you do a fresh install, you have to install all the additional software you want. if you have a separate /home, configuration files such as .bashrc, .vimrc, etc and other configuration related stuff will be retained. this way you'll have all that you have customized, as it was with the previous install. apart from that, if you keep other stuff such as documents, music, videos etc. in the /home directory, that'll of course be retained as well.

---

### Post by lykwydchykyn on 2009-03-06
What I like to do on our computers is this:
 - root partition
 - home partition
 - spare root partition

When I upgrade versions, I just alternate between using the first and second root partitions (so currently I have intrepid on one root partition, and hardy on the other).  That way I can take my time getting the new version installed with all our favorite programs and tweaks, and the old version is still usable.  And all the while, everyone has access to his/her documents and settings.

I've never been able to put together a succint bullet-point list of why a seperate home partition is a good idea, but I've almost always regretted it when I haven't done it.  Usually around the time I upgrade or reinstall.

---

### Post by Ascenti0n on 2009-03-06
how much space should I allocate for a home partition?

---

### Post by taurus on 2009-03-06
It depends on how large a harddrive you have and what kind of stuff do you plan to store in $HOME.  10GB for / should be plenty.

---

### Post by Ascenti0n on 2009-03-06
Thanks everyone for your help :D

---

### Post by Rallg on 2009-03-06
My computer has 2 copies of 8.10, with a common (separate) home directory (same user name). I only update or change one system at a time, with a delay of a couple of days between updates. That way, if I bork one system, the other one keeps working, as long as the problem is not caused by something in my home directory (unlikely).

---

### Post by Ascenti0n on 2009-03-06
This all sounds very geeky and very cool. I bet I can't do the same on a Windows box :D

---

