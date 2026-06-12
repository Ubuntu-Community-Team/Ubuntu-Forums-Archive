---
title: "Save Update Packages?"
date: 2009-04-18
forum: Installation &amp; Upgrades
---

### Post by Sum Guy on 2009-04-18
is it possible to save update packages to removable media in order to perform large updates to multiple ubuntu installations with only one download?

---

### Post by Partyboi2 on 2009-04-18
Hi, you could use something like [[COLOR=Blue]apt-cacher[/COLOR]]("http://www.debuntu.org/how-to-set-up-a-repository-cache-with-apt-cacher")

---

### Post by Paranoid Tux on 2009-04-18
You could also try to rsync the repository from your local mirror, provided that the bandwidth is free, and you are performing a large number of installs. Another option is to use CloneZilla if you are making multiple installs on machines with very similar hardware.

---

### Post by kaivalagi on 2009-04-18
Apt-zeroconf is another option

[http://michael.susens-schurter.com/blog/2006/12/12/apt-zeroconf/](http://michael.susens-schurter.com/blog/2006/12/12/apt-zeroconf/)
[http://ubuntuforums.org/showthread.php?t=796883](http://ubuntuforums.org/showthread.php?t=796883)

---

### Post by Sum Guy on 2009-04-18
thanks all

---

