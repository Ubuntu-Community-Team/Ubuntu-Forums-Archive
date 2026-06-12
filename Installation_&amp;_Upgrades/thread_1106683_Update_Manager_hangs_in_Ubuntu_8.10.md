---
title: "Update Manager hangs in Ubuntu 8.10"
date: 2009-03-25
forum: Installation &amp; Upgrades
---

### Post by LRN on 2009-03-25
Hi, I am a Linux Noob and have installed Ubuntu 8.10 on by PC.  I am attempting to run the update manager since it indicates that there are four patches that need to be installed, but when I run it and attempt to either install or check the patches the download windows pops up and nothing happens after that.  Am I missing something here?  There are not error that I can detect.

Thanks

---

### Post by Partyboi2 on 2009-03-26
Try using the terminal (Applications>Accessories>Terminal) to start update manager and install the updates, hopefully this will provide some info on what is going wrong.
```
sudo update-manager
```

---

### Post by LRN on 2009-03-27
Thank you, that works.  The update manager ran just fine, I guess you have to use the terminal interface when doing updates and not go through the system->administrator->update manager interface.  Not sure why but it works.

---

