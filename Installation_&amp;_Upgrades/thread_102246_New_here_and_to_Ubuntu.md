---
title: "New here and to Ubuntu"
date: 2005-12-11
forum: Installation &amp; Upgrades
---

### Post by NotJustANewbie on 2005-12-11
Hey, I recently (today) switched from Debian stable (using KDE) to Ubuntu Breezy after much consideration.  I have found that I love Gnome so much more than the bloated KDE. What I have found with Ubuntu is that- things just work.  I have had only a few small problems with configuring but hey, by the end of one day, I've got it running like a dream.

The only problem I see in the future is upgrading to a new Ubuntu version (away from Breezy) because I have read posts that by just changing your repositories to the new verison number screws your system up...:confused: 

Anywhoo, until that time comes... here I am, to be of any assistance.
:cool:

---

### Post by aysiu on 2005-12-11
[QUOTE=NotJustANewbie]
The only problem I see in the future is upgrading to a new Ubuntu version (away from Breezy) because I have read posts that by just changing your repositories to the new verison number screws your system up...:confused: [/QUOTE] That's been my experience, and it seems to happen about half the time. If you have a separate /home partition, a clean reinstall should be relatively painless. If you don't... maybe you should create one when Dapper comes around.

In any case, welcome!

---

### Post by NotJustANewbie on 2005-12-11
I already have a separate partition for my /home directory:

25GB - / (ReiserFS)
4GB - /home (ReiserFS)
1GB - swap

-It is a shame they haven't gone for a stable, unstable, testing versions, like Debian went for... it made so much sense

---

### Post by linbetwin on 2005-12-11
[quote=aysiu]That's been my experience, and it seems to happen about half the time. If you have a separate /home partition, a clean reinstall should be relatively painless. If you don't... maybe you should create one when Dapper comes around.

In any case, welcome![/quote]

Aysiu, what do you do about the configuration files on /home? Will they cause problems for the new install? Do you have to delete them before reinstalling?

---

### Post by NotJustANewbie on 2005-12-11
From my experience with Debian, no... the configuration files will not affect them. But thats with Debian, not Ubuntu (which is based on Debian but hey)

---

### Post by taurus on 2005-12-11
When you get to the partition stage, pick expert and tell Ubuntu to use whichever partition as / and format it.  Then, pick the one for home and have it mount on /home but tell it NOT to format it!  That's all there is...

---

### Post by NotJustANewbie on 2005-12-11
The ubuntu guys could get around this by making it like Debian. It really bugs me why they don't.

---

### Post by aysiu on 2005-12-11
[QUOTE=linbetwin]Aysiu, what do you do about the configuration files on /home? Will they cause problems for the new install? Do you have to delete them before reinstalling?[/QUOTE] No, keep them as is. They might cause a problem going from one distribution to another, but different versions within Ubuntu will be fine with those.

---

