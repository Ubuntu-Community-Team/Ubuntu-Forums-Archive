---
title: "Exporting xorg.conf"
date: 2009-07-07
forum: Installation &amp; Upgrades
---

### Post by p0cky84 on 2009-07-07
First of all I want to say sorry for not knowing where to post this question.


I'm having trouble installing xorg and getting the screen to work in ArchLinux, due to that I'm a newbie.
So is there some way I can export the configuration-files from Ubuntu 8.10 32bit existing install to a fresh ArchLinux? (on the same computer ofcourse)
And if so should I install the new nVidia drivers (I have GeForce GO 7600, which I'm pretty sure needs the G70 driver.)

My idea so far is to just ```
 cp /etc/X11/* 
``` to the other install?
Is this right?, and if so is these all the files I will need?

Sorry for the bad english and probably extreme typos I have yet to realize

---

### Post by sisco311 on 2009-07-07
Yes you can copy your xorg.conf file, but you can generate one with *hwd* (no longer supported) or with *Xorg -configure*.


The Arch Wiki is your friend:
[http://wiki.archlinux.org/index.php/Xorg]("http://wiki.archlinux.org/index.php/Xorg")

---

### Post by p0cky84 on 2009-07-07
I tried with hwd, since vbetest isn't supported in x86_64 repos.
But it didn't work, does it overwrite the current xorg.conf file or does it save it somewhere in $HOME?

---

