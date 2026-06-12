---
title: "Eh... I broke something.. again &gt;_&gt; (nVidia drivers)"
date: 2005-08-25
forum: Hardware &amp; Laptops
---

### Post by Ricapar on 2005-08-25
So, I was bored.. I downloaded the nVidia drivers from their site and installed them. Restarted X, and it all seemed to work fine. I even noticed a slight increase in FPS on some games.

Then I rebooted my computer, and was greeted with this:```
(EE) NVIDIA(0): Failed to load the NVIDIA kernel module!
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(EE) Screen(s) found, but none have a usable configuration.
```

I was able to get back into X by changing the [font=Courier New]Driver "nvidia"[/font] line back to the default "nv" setting, though now everything is slow.

So.. any ideas? I've already done [font=Courier New]aptitude reinstall nvidia-glx nvidia-kernel-common [font=Verdana]but I stll get the error mentioned above when I try to start up X.[/font][/font]

---

### Post by zlogic on 2005-08-25
When you reinstall a package, it's config files remain unchanged, I figured it out after trial and error.
Try removing and then installing these packages back, I think nothing depends on them. Or you can manually copy the configuration files from the .deb packages.

---

### Post by markthecarp on 2005-08-25
[QUOTE=Ricapar]
So.. any ideas? I've already done [font=Courier New]aptitude reinstall nvidia-glx nvidia-kernel-common [font=Verdana]but I stll get the error mentioned above when I try to start up X.[/font][/font][/QUOTE]

Another possibility is that an "nvidia" line wasn't added to your /etc/modules file. 

-mark

---

