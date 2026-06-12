---
title: "Sporadic respawning of certain processes after termination"
date: 2008-09-11
forum: General Help
---

### Post by [Ad0] on 2008-09-11
Well the topic says it all. :-)

I have this most strange issue with certain applications (XBMC (xbmc.bin) and vdr-sxfe are getting respawned upon termination.
It only happens after 2-3 terminations. Never the first one! (!!!)

Is there something in ubuntu linux, gnome or anything that monitors dirty process exits and just reopen them without asking?

When running pstree, I don't see any process that has launched it. I have have 7 instances of xbmc.bin on first level (init) (it says 7*[xbmc.bin]) and xbmc.bin--3*[xbmc.bin].
I haven't tried pstree on vdr-sxfe, since I stopped using it.

On vdr-sxfe I got as much as 100 processes! Can it be the applications doing it themselves or can it be something in the OS? When running ps aux --forest, they all go on the noot node so they aren't child processes of anything.


Thanks in advance!

---

### Post by [Ad0] on 2008-09-11
I am using a standard installation of Ubuntu Desktop 8.04.

---

### Post by [Ad0] on 2008-09-15
*Bump*

---

### Post by [Ad0] on 2008-10-03
Solved. It seems like gnome or something is treating my remote as a keyboard. The remote tends to hang itself up sometimes, so disabling keyboard repeat rate in keyboard settings fixed the problem!

Is it possible to disable the remote as a keyboard?

---

