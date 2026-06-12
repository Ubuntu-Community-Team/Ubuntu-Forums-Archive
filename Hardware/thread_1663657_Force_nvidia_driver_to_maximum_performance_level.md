---
title: "Force nvidia driver to maximum performance level"
date: 2011-01-09
forum: Hardware
---

### Post by gufide on 2011-01-09
Hi, my nvidia driver limit my gpu clock and it make lag my animation at else I make the expo or something that it take gpu performance. I don't like this, it limi my gpu to 135mHz and memory to 135 mHz on level 0 to and it make scrolling slow and laggy. There's a way to force it to get only on performance level 1 or 2? I select the mode maximum performance, but it change nothing :(
Thank you

---

### Post by cascade9 on 2011-01-09
What video card, and what drivers?

---

### Post by gufide on 2011-01-10
NVidia geForce gts 360m
Driver: nvidia proprietary driver 256.53

---

### Post by efflandt on 2011-01-11
How did you end up with that older nvidia driver, are you running a pre-release version of Maverick?  People with some nvidia cards had lag trouble with that driver version, which sounds like your problem.  So it was changed to a 260 version before Maverick was released.

I don't know which nvidia-current version is in Maverick at the moment.  But if you need a newer version than that, the x-swat repositories usually have the most recent version.  [http://www.ubuntuupdates.org/ppas/27](http://www.ubuntuupdates.org/ppas/27)

But without knowing how you installed the version you have, I don't know if it is as simple as adding the repository, doing updates, and installing nvidia-current, nvidia-settings, and nvidia-current-modaliases, or if you need to undo something else if the version you have now was from the nvidia website instead of Ubuntu repositories.

---

### Post by gufide on 2011-01-11
> **efflandt said:**
> How did you end up with that older nvidia driver, are you running a pre-release version of Maverick?  People with some nvidia cards had lag trouble with that driver version, which sounds like your problem.  So it was changed to a 260 version before Maverick was released.

I don't know which nvidia-current version is in Maverick at the moment.  But if you need a newer version than that, the x-swat repositories usually have the most recent version.  [http://www.ubuntuupdates.org/ppas/27](http://www.ubuntuupdates.org/ppas/27)

But without knowing how you installed the version you have, I don't know if it is as simple as adding the repository, doing updates, and installing nvidia-current, nvidia-settings, and nvidia-current-modaliases, or if you need to undo something else if the version you have now was from the nvidia website instead of Ubuntu repositories.

no, it's not the beta version, I install a stable due to some issue

---

### Post by gufide on 2011-01-12
no one?

---

