---
title: "Hoary to Breezy"
date: 2005-12-11
forum: Installation &amp; Upgrades
---

### Post by JoshHendo on 2005-12-11
What is the best way to upgrade ubuntu without loosing all my data? Is there a way to just upgrade everything, or do I need to format and do a fresh install :|? If that is the case, I can place everything on my mp3 player for temp storage, though it would be better if I didn't have to do something like that =p. Thanks :)

-Josh

---

### Post by dcast on 2005-12-11
You can upgrade right from the cd however I did it and my system was totalley borked so I would just do a fresh install

---

### Post by aysiu on 2005-12-11
I, too, have had no luck doing an upgrade. A fresh install worked best. However, I know others have been able to upgrade with no problems. If you've already backed up your data, it's worth a shot. Change your sources.list to the Breezy set (see the first link of my sig) and then ```
sudo apt-get update
sudo apt-get dist-upgrade
``` If you do reinstall, consider creating a separate /home partition so that you can easily reinstall without losing your data and settings.

---

### Post by mhoskins on 2005-12-11
[QUOTE=dcast]You can upgrade right from the cd however I did it and my system was totalley borked so I would just do a fresh install[/QUOTE]

My system borked also - choaked on a ppp upgrade, and it has been a while since I've used a modem. The worst news is that this is my wife's computer. Let's discuss 'unpopular'shall we? Just shoot me.

Sony Viao PCG-R505JL

---

