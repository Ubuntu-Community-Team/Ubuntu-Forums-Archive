---
title: "old packages in repos"
date: 2009-01-30
forum: Installation &amp; Upgrades
---

### Post by manualqr on 2009-01-30
Hello,

I've noticed that packages in 8.10 are generally older than packages shipped by other distros.
I recognize the need for stability, but I think the best way to improve it would be to ship more mature versions of code.

Deluge, for example, is at 1.1.1, and the latest Ubuntu package is 0.5.9.3.
Geany is at .15, and the Ubuntu package is at .14.

Are there solutions, such as unofficial repos, that can provide newer packages?

thank you for your time
-mqr

---

### Post by slakkie on 2009-01-30
Yes, and they are called PPA (personal package archives). Or you could download the sources of these applications and compile them yourself, install them using checkinstall and you are good to go.

For information about checkinstall:

aptitude -D show checkinstall and man checkinstall (if you have installed it).

---

### Post by ibutho on 2009-01-30
Hi and welcome to the forums. 

In the case of Deluge, they provide packages for various Ubuntu versions, so you can just download the latest version and install using dpkg or gdebi.

---

### Post by manualqr on 2009-01-31
>  Hi and welcome to the forums. 

thank you! I really appreciate this as most other forums welcome me with trolling..

The Deluge .deb tip was great as well.

// edit
I found the PPA information, thanks!

---

