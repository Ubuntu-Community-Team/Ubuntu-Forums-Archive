---
title: "how to uninstall &quot;depends&quot; apps in ubuntu-studio-dekstop"
date: 2008-07-25
forum: General Help
---

### Post by silicium on 2008-07-25
Hi, I am coming to ubuntu-studio, from the FreeBSD world where there is a lack of interest for multimedia. I was  used to install a small OS then choose only the applications that I need and will have time to learn. But I found ubuntu-studio disappointing because it is bloated with software that I will never use, at least on my intended studio computer (gnome-pilot-*, avahi-*, gnome-spell to name a few). When I force remove them, the dependency tree is broken and I can't install new useful *.deb packages anymore. I am stuck with ubuntu studio because of the long time I spent hacking to get working drivers for my M-Audio USB devices. Does anyone know how to edit the dependency tree before or after installation so I won't feel like going back to W2K :confused: ? Thanks for installer hacking tips !

---

### Post by ProbablyX on 2008-07-25
Gnome pilot? Are you installing Evolution? If so, it might not be the perfect solution - but there are other programs for instance Mozilla Thunderbird in that case that does not need all the same apps.
You can always change to another software that requires less stuff :)

---

### Post by stanley82 on 2008-07-25
If you installed using the package manager you can uninstall using the package manager.
If you installed from tarball using
./configure
make
sudo make install   then
sudo make uninstall should do the trick.

---

### Post by decoherence on 2008-07-25
Why do you have to force remove them?

The -desktop packages are metapackages that install a broad range of programs that are useful to most people. If you want a special-purpose system the -desktop packages are not for you.

Just uninstall whatever you don't want. The dependancy tree shouldn't break if you don't force anything but you may find you need to do some juggling if you're making drastic changes. If you have trouble, post the errors here; you'll get help.

Ubuntu is an extremely flexible system. It just tries to be a general OS by default, even ubuntu studio.

---

