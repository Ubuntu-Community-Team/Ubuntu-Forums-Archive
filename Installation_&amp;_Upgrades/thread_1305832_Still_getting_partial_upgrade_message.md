---
title: "Still getting partial upgrade message"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by RobsterUK on 2009-10-30
I'm running an install of the last beta (not RC) without any updates and update manager still only giving me the option of a partial upgrade, which I thought would be resolved by package issues settling down after the full release.

I've avoided doing any updates after breaking my install from running a partial upgrade before (lesson learned there)

Any ideas on how to resolve this?

---

### Post by RobsterUK on 2009-11-02
Sorry to bump, but anyone have any ideas on this? Its a few days after full release now, and I've still got this issue, so something is not quite right.

---

### Post by ubun209 on 2009-11-02
I installed 9.10 with WinXP and 9.04. It added another partition with 9.10. I was hoping it would upgrade my 9.04 but I may have done something wrong. Anyways, I got rid of WinXP (I am sooo happy) and 9.04 and installed 9.10 from scratch.

---

### Post by japsai on 2009-11-02
I am having the same issue as the topicstarter.

apt-get upgrade:
```
The following packages have been kept back:
  libpulse-browse0 libpulse-mainloop-glib0 libpulse0 pulseaudio 
  pulseaudio-esound-compat pulseaudio-module-bluetooth 
  pulseaudio-module-gconf pulseaudio-module-udev pulseaudio-module-x11 
  pulseaudio-utils ubuntu-desktop 
0 packages upgraded, 0 newly installed, 0 to remove and 11 not upgraded.
```

Does anyone know what we should do? Is it safe to do the partial-upgrade now?

---

### Post by RobsterUK on 2009-11-02
japsai that's a useful output I hadn't thought of, mine is:

```
The following packages have been kept back:
  evolution-plugins ibus libpulse-browse0 libpulse-mainloop-glib0 libpulse0
  linux-generic linux-headers-generic linux-image-generic
  openoffice.org-base-core openoffice.org-calc openoffice.org-core
  openoffice.org-draw openoffice.org-gnome openoffice.org-gtk
  openoffice.org-impress openoffice.org-math openoffice.org-writer pulseaudio
  pulseaudio-esound-compat pulseaudio-module-bluetooth pulseaudio-module-gconf
  pulseaudio-module-udev pulseaudio-module-x11 pulseaudio-utils python-ibus
  python-uno ubuntu-desktop xserver-xorg-input-all
The following packages will be upgraded:

```
followed by a long list of packages...

---

### Post by japsai on 2009-11-04
Did you find a solution yet, RobsterUK?

---

### Post by RobsterUK on 2009-11-04
> **japsai said:**
> Did you find a solution yet, RobsterUK?

No I'm afraid not, its looking like I may have to download the ISO of the full release and do a clean install, but that seems excessive, hopefully there's another way round it.

---

### Post by japsai on 2009-11-16
I still have this problem and a full reinstall is way too much work really..

What would happen if we just do this "partial upgrade" thing?

---

### Post by Aereal on 2009-11-17
Same thing happening to me, I've done this and got to move on... but... maybe you can check it out

[http://ubuntuforums.org/showthread.php?p=8326965#post8326965](http://ubuntuforums.org/showthread.php?p=8326965#post8326965)

---

### Post by japsai on 2009-11-18
I performed the "partial upgrade" and this worked for me, only two packages were removed and apparently that was correct.

---

