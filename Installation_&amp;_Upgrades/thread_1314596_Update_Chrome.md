---
title: "Update Chrome"
date: 2009-11-04
forum: Installation &amp; Upgrades
---

### Post by Nima1972 on 2009-11-04
Hi, thanks for looking into this.

I have Google Chrome dev edition installed on Ubuntu 9.10.

How do I update Chrome to the latest available edition?

---

### Post by Paul41 on 2009-11-04
I'm not sure how you installed it but if you follow this guide it will be updated for you with a apt-get upgrade (or through the update manager).

[http://www.ubuntugeek.com/how-to-install-chromium-google-chrome-in-ubuntu-using-deb-package.html](http://www.ubuntugeek.com/how-to-install-chromium-google-chrome-in-ubuntu-using-deb-package.html)

---

### Post by Nima1972 on 2009-11-04
Paul, that's exactly how I installed it.  Which part do I need to run for the upgrade?  Not the whole thing I imagine.

---

### Post by Paul41 on 2009-11-04
If you run the following in the terminal it will get any updates.

```
sudo apt-get update && sudo apt-get upgrade
```

Even though they are "nightly builds" there are some nights where there are no upgrades. The latest build is 4.0.233.0 (Ubuntu build 30813).

---

