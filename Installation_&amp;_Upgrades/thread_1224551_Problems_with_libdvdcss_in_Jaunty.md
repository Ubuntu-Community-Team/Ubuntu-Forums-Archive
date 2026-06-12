---
title: "Problems with libdvdcss in Jaunty"
date: 2009-07-27
forum: Installation &amp; Upgrades
---

### Post by Joshka89 on 2009-07-27
Hi. I have recently installed Ubuntu 9.04 Jaunty.

I went to [http://www.debian-unofficial.org/](http://www.debian-unofficial.org/) and downloaded libdvdcss2.deb and used the package installer to install it.

I checked my system and it is in fact listed as now being installed on my machine.

Still, when i use Xine to run my DVD is gives me the error:

The source seems encrypted and can't be read. Are you trying to play an encrypted DVD without libdvdcss?

Help?

---

### Post by vinutux on 2009-07-27
use **vlc** ```
sudo apt-get install vlc
``` and install libdvdcss2 from mediubuntu repo **[www.medibuntu.org/]("www.medibuntu.org/")**

---

### Post by Ratscallion on 2009-07-27
See this: [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by Joshka89 on 2009-07-27
thanks that worked. I already had libdvdcss2 but the vlc player actually acknowledged it.

---

