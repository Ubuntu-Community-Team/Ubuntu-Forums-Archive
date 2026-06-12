---
title: "Jaunty upgrade: use non-boot partition."
date: 2009-04-23
forum: Installation &amp; Upgrades
---

### Post by HonoredMule on 2009-04-23
I'm trying to upgrade 8.10 to 9.04 on an Aspire One, which has a root partition of about 3.7G (/home taking the rest, but mostly empty).  Upgrade fails because there is insufficient disc space to download the new packages. 

How can I tell the update-manager to use a path on the other partition or an external USB/SD drive to download the updates, or alternately, what directory can I make into an external mount point to provide the needed space?  I'm quite confident that there is actually enough space to perform the upgrade if would just not try to cache the data on the boot partition before using it to overwrite existing files.

TIA

---

### Post by HonoredMule on 2009-04-23
I mounted a 2 GB SD card at /var/cache/apt, and that appears to have done the trick (I'm past the insufficient space error, at least).  I did have to format the card as ext and copy the original contents, though I'd assume there was some apt command I could have used to rebuild the cache.

UPDATE:  To anyone else that tries this, note that using an SD card really slows things down.  The actual installation is taking me about 5 hours.  I'm now wishing I had gone to the trouble of digging out my external hard drive.

---

