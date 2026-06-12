---
title: "Compiz and AWN broke after upgrade to Intrepid"
date: 2008-11-05
forum: General Help
---

### Post by fracktor on 2008-11-05
After upgrading from Hardy to Intrepid my compiz and awn are not working. Awn will show up in the system monitor like its running, but it never actually loads. The same goes for compiz. I have tried removing and reinstalling both to no avail. I have also tried different nvidia drivers. None of that has helped. If I run compiz-check I get the following output...
 Distribution:          Ubuntu 8.10
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation NV34 [GeForce FX 5500] (rev a1)
 Driver in use:         vesa
 Rendering method:      None
Checking if it's possible to run Compiz on your system...  [SKIP]

At least one check had to be skipped:
 Error: No rendering method in use (AIGLX, Xgl or Nvidia) 


Any help is greatly appreciated.

---

### Post by fracktor on 2008-11-06
I wanted to also add, that I also tried using envy as well for installing the nvidia drivers but that did not seem to help either. I don't know if the same reason that compiz is not working is related to why AWN is not working.

---

### Post by fracktor on 2008-11-08
I think I may have found out what is going on. Their seems to be an issue with the new X and ceartin nvidia cards. I found this posting that may help whats going on for other people with similar issues...
[http://nxadm.wordpress.com/2008/10/31/bug-ubuntu-810-and-older-nvidia-video-cards/](http://nxadm.wordpress.com/2008/10/31/bug-ubuntu-810-and-older-nvidia-video-cards/)

---

