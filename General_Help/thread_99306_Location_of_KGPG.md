---
title: "Location of KGPG?"
date: 2005-12-05
forum: General Help
---

### Post by gustavo1985 on 2005-12-05
First off, I'd like to say how great Kubuntu is. As a former Slackware user, its great that everything "just works." Simply put, it is a great desktop distribution.

On to the question....

What specific package installs the kgpg tool? I thought it was installed by default but I can't seem to find it. Could anyone point me in the right direction?

Thanks

---

### Post by daller on 2005-12-05
Isn't it "kgpg" ???

This is in danish, but I hope you get it...

```

madsen@ubuntu:~$ sudo apt-get install kgpg
Indl&#230;ser pakkelisterne... F&#230;rdig
Opbygger afh&#230;ngighedstr&#230;... F&#230;rdig
F&#248;lgende NYE pakker vil blive installeret:
  kgpg
0 opgraderes, 1 nyinstalleres, 0 afinstalleres og 0 opgraderes ikke.
454kB skal hentes fra arkiverne.
Efter udpakning vil 1376kB yderligere diskplads v&#230;re brugt.
Henter:1 http://kubuntu.org breezy/**main** kgpg 4:3.5.0-0ubuntu0breezy1 [454kB]
Hentede 454kB p&#229; 8s (53,1kB/s)

Pr&#230;konfigurerer pakker ...
V&#230;lger tidligere fravalgt pakke kgpg.
(L&#230;ser database... 103409 filer og mapper aktuelt installeret.)
Udpakker kgpg (fra .../kgpg_4%3a3.5.0-0ubuntu0breezy1_i386.deb)...
S&#230;tter **kgpg** (3.5.0-0ubuntu0breezy1) op...


```

Find it here:

Kmenu -> Tools -> PIM -> KGPG (Translated from danish!)

---

### Post by gustavo1985 on 2005-12-05
gat@blackbetty:~$ sudo apt-get install kgpg
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package kgpg


KMenu -> Tools doesn't exist on my system. Any other ideas?

---

### Post by gustavo1985 on 2005-12-05
OK nevermind I found it after I added more repositories to /etc/apt/sources.list

Thanks for the help anyways:)

---

