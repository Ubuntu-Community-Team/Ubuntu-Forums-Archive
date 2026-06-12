---
title: "Stability problems with compiz and nvidia 173.14.09"
date: 2008-07-11
forum: General Help
---

### Post by jeromio on 2008-07-11
I had some strange stability issues with nvidia 173.14.05: compiz would crash often. So I upgraded to 173.14.09. Now, compiz consumes too much CPU. Just sitting, it will hover at 5%, but it frequently spikes to 80% and will spend time between 20-50%. I have a dual core AMD64 system, so something is not right.

Worse, in the 5 days that I have used this driver, a previously stable system has locked up 4 times. Not just X, the whole system (external ssh sessions dead also).

I don't see anything in the logs associated with the lockups. At one point, the system started dieing more slowly. One window locked up, then another, then I ran top and bash said no such command. Same for ps. The ls command gave an error about some missing library. Crazy. shortly after that the whole system locked up.

If I disable compiz, the system is much more stable. But it's also much more boring...

Anyone have any tips for debugging this or maybe some config options I could try?
```
jeromio@blirp:/home/downloads$ compiz-check

Gathering information about your system...

 Distribution:          Ubuntu 8.04
 Desktop environment:   KDE
 Graphics chip:         nVidia Corporation C51 [GeForce 6150 LE] (rev a2)
 Driver in use:         nvidia
 Rendering method:      Nvidia

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]
```

---

