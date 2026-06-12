---
title: "Changing Date Display Format"
date: 2008-07-23
forum: General Help
---

### Post by cmnorton on 2008-07-23
Is it possible to change this format 

 2008-07-23 14:54 nohup.out

to this format 
 
 Jul 23 14:54 nohup.out

I have looked through my Kubuntu settings, but did not see anything readily that would allow me to change the display behavior. The format I want is from Fedora. Our production systems are Red Hat; I do my development on Kubuntu, and would like certain things like date extracts to be uniform.

I could always kludge things by having the shell script look for the /etc/rc.d directory and, not finding that, extract the date differently, but I would prefer to change the date display format.

Edit:
----------------------------------------------------------------------------------------------------------------

I want something like this:


$ ls -l --time-style +'%b %d' nohup.out
-rw------- 1 ics ics 58 Jul 23 nohup.out

But, like Fedora, I'd like years to show up when the year value is older than this year.

---

### Post by MatthiasHeil on 2008-07-23
Alt+F2
gconf-editor

set key
/apps/panel/applets/clock_screen0/prefs/format
to custom

and
/apps/panel/applets/clock_screen0/prefs/custom_format
to e.g. %A, %d. %B %G, %H:%M:%S

Hope that helps - not sure this wholly solves your problem, however...-)

---

