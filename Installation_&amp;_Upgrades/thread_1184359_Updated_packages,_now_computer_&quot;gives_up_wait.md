---
title: "Updated packages, now computer &quot;gives up waiting for root device&quot;"
date: 2009-06-11
forum: Installation &amp; Upgrades
---

### Post by scearley on 2009-06-11
I've been trying to update the packages on my subnotebook for some time, and they would consistently fail over the past month because of a "break," in the dependencies, I presume.  Upgrades to 9.04 altogether failed for the same reason after adept told me it couldn't update my packages.

Elsewhere I saw that I should run
```
sudo apt-get update && sudp apt-get upgrade
```

And post the error messages, however, once I did this, it updated fine, I got no error messages, and then got an alert that I should reboot.  So I did.

Now the computer boots, goes through a new Kubuntu splash (though similar to before, the progress bar is slightly different, the graphics are smaller), then I am given a screen full of errors and dumped to shell.

```
usplash: Setting mode 1152x864 failed
usplash: Setting mode 1024x768 failed
usplash: using mode 800x600
Gave up waiting for root device. Common problems:
(here it lists boot args, check root delay, check root, missing modules)

ALERT! /dev/disk/by-uuid/(enormous string) does not exist. Dropping to a shell!
```

And I'm at a shell.  I have no idea where to go from here.  Obviously I can't 'startx' or anything similar.  

I get the sinking feeling, after all of the previous complete failures I've gone through with just trying to get Ubuntu to work on various machines, despite everyone's telling me how wonderful it is, that I have now bricked this one.

---

