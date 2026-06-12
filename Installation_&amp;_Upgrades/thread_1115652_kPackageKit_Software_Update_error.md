---
title: "kPackageKit Software Update error"
date: 2009-04-04
forum: Installation &amp; Upgrades
---

### Post by dasme on 2009-04-04
Hi all,
Just installed kubuntu 9.04 beta and updated it using kpackagekit, during scan it told me that 304 new updates are available. I updated it using apply all available update button.

All went well it asked me to reboot. After reboot when i pressed the refresh button to check more updates it gave me this error.

"Refreshing cache failed: W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty/main/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/jaunty/main/binary-i386/Packages.bz2)  Hash Sum mismatch
, E:Some index files failed to download, they have been ignored, or old ones used instead."

Pls help, now i am unable to update my system.

Thx

---

### Post by zvacet on 2009-04-04
In terminal

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by giacof on 2009-04-10
Same problem here. Now Software Updates reports 3 blocked updates that cannot be downloaded.
The same error occurs when trying to update from the console with the command shown above.

---

