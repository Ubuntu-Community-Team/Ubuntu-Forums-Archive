---
title: "My experience: 9.04 -&gt; 9.10 -&gt; 9.04"
date: 2009-11-01
forum: Installation &amp; Upgrades
---

### Post by carlholmberg on 2009-11-01
Hi, I tried to upgrade my old Fujitsu-Siemens Amilo M7400 to 9.10 but sadly it failed.

The graphics adapter (Intel 855GM) seems to be quite incompatible with the new X-server and drivers. I tried to manually configure a xorg.conf-file, but no luck whichever way I tried. The screen just randomly freezes and I can't even switch to an emergency shell or get X to restart.

Also, because the network adapter isn't automatically found, I wasn't able to connect to my Wifi to try to install a new (and unstable) version of the X-server or install the intel-debug-package.
To get my wifi to work I still have to manually add "wistron_btns" to the "etc/modules"-file and I can't seem to be able to get it working from a shell.

The freezing started sometime during 9.04 so the only solution I've found so far is to keep 9.04 but with X-server kept back to the version from 8.10. This gives me a stable system, but won't let me upgrade to 9.10 (some kind of forced dependency on the new X-server). I have tried some experimental versions of Xorg under 9.04 but nothing helped.

So, if you have a older laptop with a graphics adapter from Intel, you might not be able to run 9.10.

Actually it doesn't matter much 'cause we will be replacing the laptop some time soon, but still it is irritating not to be able to get it to work!

/Carl

---

