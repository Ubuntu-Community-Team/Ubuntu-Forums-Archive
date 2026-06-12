---
title: "Updating synaptic package manager?"
date: 2008-11-08
forum: General Help
---

### Post by mr nintendo on 2008-11-08
is it possible to update all of the packages in synaptic package manager?
because I have noticed  that when I search for something on synaptic then I install that particular program the version it shows is usually older then newer versions on the internet.

```
sudo apt-get update
```
doesn't seem to fix this :(

---

### Post by ad_267 on 2008-11-08
No. The versions in Synaptic depend on the versions in the Ubuntu repository. These are often not the latest version, but versions that have been tested thoroughly and packaged. If you want new versions of stuff then you have to download a .deb or compile it yourself. You could also enable the backports repository. This page will explain some stuff for you: [https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports). Upgrading to Ubuntu 8.10 should also get newer versions.

---

### Post by mr nintendo on 2008-11-08
Thanks, I think I got what I was looking for

---

