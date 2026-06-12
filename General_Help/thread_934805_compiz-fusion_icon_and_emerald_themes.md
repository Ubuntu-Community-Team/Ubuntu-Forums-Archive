---
title: "compiz-fusion icon and emerald themes"
date: 2008-10-01
forum: General Help
---

### Post by bluet0oth on 2008-10-01
i recently installed a new comp/and laptop with hardy, but they have the same repository info and differant things r on the laptop that arn't on the comp, i want the compiz-fusion icon, and the emerald themes... neither show in in the repository lists on the main computer for some reason

ne ideas??

---

### Post by overdrank on 2008-10-01
> **bluet0oth said:**
> i recently installed a new comp/and laptop with hardy, but they have the same repository info and differant things r on the laptop that arn't on the comp, i want the compiz-fusion icon, and the emerald themes... neither show in in the repository lists on the main computer for some reason

ne ideas??

HI and have you checked the sources list
```
gksu gedit /etc/apt/sources.list
``` to ensure that some repos are not commented out with #.
What is the error when trying to install fusion icon. or are you searching from synaptic manager.

---

### Post by anotherdisciple on 2008-10-01
I don't know if this is the issue, but the package is called "fusion-icon" instead of "compiz-fusion-icon"... other than that... I would check your sources.list just like overdrank said

---

