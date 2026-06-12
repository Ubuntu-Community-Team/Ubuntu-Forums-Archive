---
title: "[SOLVED] Kubuntu logo after installing the package &amp;quot;kubuntu-desktop&amp;quot;"
date: 2008-08-09
forum: General Help
---

### Post by Pidgin on 2008-08-09
I want to use both GNOME and KDE in one system. So I installed the package "kubuntu-desktop" on my Ubuntu. (Is that right?) Then I found that the starting Ubuntu logo had been replaced by the Kubuntu logo. What should I do to get the original logo back?
Thanks!

---

### Post by Elfy on 2008-08-09
There are a couple of options here that should do that for you

[http://ubuntuforums.org/showthread.php?t=428061](http://ubuntuforums.org/showthread.php?t=428061)

---

### Post by vishzilla on 2008-08-09
this should correct it
```
sudo update-alternatives --config usplash-artwork.so
sudo update-initramfs -u
```

---

