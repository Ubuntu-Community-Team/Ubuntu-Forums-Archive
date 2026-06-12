---
title: "problem with last upgrade dbus and/or restricterd modules common 2.6.24-21.51"
date: 2008-10-12
forum: General Help
---

### Post by harvixen on 2008-10-12
hi all..
i seem to have really strange problem after last update. what happens is that after watching flash videos after sometime they hang and stutter and continue after i press space or any other key. also the progress bar when restarting is also reacting when i press space-bar. compiz after sometime becomes jerky and lags..seems like its has some memory polling/leak issues there..

as in title i upgraded from:

linux-restricted-modules-2.6.24-21-generic (2.6.24.14-21.50) to 2.6.24.14-21.51
linux-restricted-modules-common (2.6.24.14-21.50) to 2.6.24.14-21.51
dbus (1.1.20-1ubuntu2) to 1.1.20-1ubuntu3
dbus-x11 (1.1.20-1ubuntu2) to 1.1.20-1ubuntu3
libdbus-1-3 (1.1.20-1ubuntu2) to 1.1.20-1ubuntu3
libdbus-1-dev (1.1.20-1ubuntu2) to 1.1.20-1ubuntu3
libffi4 (4.2.4-1ubuntu1) to 4.2.4-1ubuntu3
libffi4-dev (4.2.4-1ubuntu1) to 4.2.4-1ubuntu3
libgcc1 (1:4.2.4-1ubuntu1) to 1:4.2.4-1ubuntu3
libgcj8-1 (4.2.4-1ubuntu2) to 4.2.4-1ubuntu3
libgcj8-1-awt (4.2.4-1ubuntu2) to 4.2.4-1ubuntu3
libgcj8-dev (4.2.4-1ubuntu2) to 4.2.4-1ubuntu3
libgcj8-jar (4.2.4-1ubuntu2) to 4.2.4-1ubuntu3
libgomp1 (4.2.4-1ubuntu1) to 4.2.4-1ubuntu3

my system is 8.04.1 ubuntu, ati catalyst 8.9, compiz 0.7.7 updated and running fine untill a day ago.

i think it is issue with linux-modules but i could be wrong ..first thing that comes to my mind is also dbus issue..dunno.

anyone has the same issue? 

any clue would be welcome.
thanx.

---

### Post by harvixen on 2008-10-13
hi ..
just the quick update:

my problem with stuttering and lagging in sound, flash and windows moving/opening/closing doesn't occur with older 2.6.24-20 kernel and its modules..so i would track it down to restricted modules-common 2.6.24-21.51 

so nobody has the same problems? strange.

---

