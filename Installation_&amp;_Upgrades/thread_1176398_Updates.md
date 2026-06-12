---
title: "Updates"
date: 2009-06-02
forum: Installation &amp; Upgrades
---

### Post by gandalf458 on 2009-06-02
Since I ran a manual apt-get update, I'm not getting any automatic updates. When I run update manager it tells me my system is up-to-date but when I press Check it usually finds some updates. And I always have gstreamer0.10-plugins-bad greyed out.

Any ideas what's wrong please?

---

### Post by MichaelSammels on 2009-06-02
Try doing this:

```
sudo dpkg --configure -a
```
```
sudo apt-get update
```

Also, make sure that you reboot. If you are having problems with the gstreamer-0.10-plugins-bad, open Synaptic, search for it and reinstall it.

---

### Post by gandalf458 on 2009-06-02
Thanks.
G :)

---

### Post by gandalf458 on 2009-06-10
I'm still getting the same problem. In addition, although I understand OOo 3.1 is out I'm not being offered this upgrade.

---

