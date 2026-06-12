---
title: "gnome (?) keeps crashing"
date: 2008-10-10
forum: General Help
---

### Post by Mzwo on 2008-10-10
hi,

i've encountered the following problem:

out of the blue and seemingly unrelated to the task being performed at the time (anything from running jack, ardour and hydrogen to just sitting around in idle) i'm confronted with a black screen, followed by a list of processes (none of which i understand, i'm afraid. one included alsa and timidity. or something) which are declared to be [ok]. 

i tried crtl+alt+bksp - no luck. ctrl+alt+f5 will let me log in, but 

sudo /etc/init.d/gdm restart 

won't let me back into my desktop. neither does

sudo /etc/init.d/gdm start

or

sudo /etc/init.d/gdm stop

i do get messages confirming that gnome is being stopped/started/restarted, but nothing happens. 

any ideas?

i'm running hardy studio, kernel 2.6.24-19-rt, gnome 2.22.3 on a toshiba satellite. the system has been set up only very recently and not been mucked about with - with the exception of installing a tascam us-122, which involved a lot of "firmwares". like so: [https://help.ubuntu.com/community/TASCAM_US-122](https://help.ubuntu.com/community/TASCAM_US-122). sorry if this is a little unspecific, i'm merely a dumb user ... 

any help very much appreciated.

Mzwo

---

### Post by Mzwo on 2008-10-10
update:

it just happened again. the messages i get are:

*starting anac(h)ronistic cron anacron       [OK]
*starting deferred execution scheduler atd   [OK]
*starting periodic command scheduler crond   [OK]
*checking battery state...                   [OK]
running local boot scripts (/etc/rc.local)   [OK]
*starting Timidity ........ before i could finish typing this (am using my desktop) the messages dissappered.  this last message also said something about alsa, and the mysterious [OK]

all i can see now is a black screen. 

help??

Mzwo


PS: crtl+alt brought the messages back up. last line reads:

*starting TiMidity++ ALSA midi emulation...           [OK]

kinda need urgent help since a project is due soon...


PPS: also, the intervals between hangups appear to become shorter.

and finally PPPS: i'm presented with a blinking cursor after the messages. i can type stuff, but nothing happens.

---

### Post by Mzwo on 2008-10-12
bump

---

