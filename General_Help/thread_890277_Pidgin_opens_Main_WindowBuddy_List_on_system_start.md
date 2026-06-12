---
title: "Pidgin opens Main Window/Buddy List on system startup"
date: 2008-08-14
forum: General Help
---

### Post by Sam324 on 2008-08-14
Hi.  Whenever I start up my computer, Pidgin opens its main window.  I don't want this;  I just want it to run and sign me in silently.  I set it up in Sessions to run the command "pidgin".  What do I do?  Is there any special argument I need to use?

---

### Post by Mgiacchetti on 2008-08-14
got a workaround...

When you log off, click the x in the window for pidgin.

Then you can either right click the sys tray icon, close or log off.

It should start the same way it last closed, if that makes sense.

---

### Post by drs305 on 2008-08-15
in synaptic there is a pidgin plugin called pidgin-extprefs that has an option of starting with the buddy list minimized. It works for some but not for everyone.

Install it via synaptic:
```
sudo aptitude install pidgin-extprefs
```

Start pidgin > tools > plugins > Extended Preferences 0.7 > Configure Plugin > Hide Buddy List at startup.

Some can hide the buddy list if started normally but not if initiated from Sessions. If the above doesn't work, here is a thread with a possible workaround:
[http://ubuntuforums.org/showthread.php?t=465590#10]("http://ubuntuforums.org/showthread.php?t=465590#10")

---

### Post by Disabled20240622 on 2009-05-20
> **drs305 said:**
> in synaptic there is a pidgin plugin called pidgin-extprefs that has an option of starting with the buddy list minimized. It works for some but not for everyone.

Install it via synaptic:
```
sudo aptitude install pidgin-extprefs
```

Start pidgin > tools > plugins > Extended Preferences 0.7 > Configure Plugin > Hide Buddy List at startup.

Some can hide the buddy list if started normally but not if initiated from Sessions. If the above doesn't work, here is a thread with a possible workaround:
[http://ubuntuforums.org/showthread.php?t=465590#10]("http://ubuntuforums.org/showthread.php?t=465590#10")

I tried the wrapper script from that thread, needed 10 seconds however (EEE 901).

```

#!/bin/sh
sleep 10;
/usr/bin/pidgin

```

---

### Post by shadarack on 2009-12-28
None of that worked for me, but what did was:

tools> plugins> Buddy List Options 2.6.0> Configure Plugin> Hide the buddy list when it is created

Thought I'd share just in case this was frustrating anyone else.

---

### Post by cwhisperer on 2010-01-04
> **drs305 said:**
> in synaptic there is a pidgin plugin called pidgin-extprefs that has an option of starting with the buddy list minimized. It works for some but not for everyone.

Install it via synaptic:
```
sudo aptitude install pidgin-extprefs
```

Start pidgin > tools > plugins > Extended Preferences 0.7 > Configure Plugin > Hide Buddy List at startup.

Some can hide the buddy list if started normally but not if initiated from Sessions. If the above doesn't work, here is a thread with a possible workaround:
[http://ubuntuforums.org/showthread.php?t=465590#10]("http://ubuntuforums.org/showthread.php?t=465590#10")

this worked for me! :)

one problem still persists: when I close the Buddy List window with X, the pidgin application is closed completely. How to change this so that pidgin will only close on exit? Thx in advance for any help...

---

### Post by Kevinlittleton on 2010-01-07
> **cwhisperer said:**
> this worked for me! :)

one problem still persists: when I close the Buddy List window with X, the pidgin application is closed completely. How to change this so that pidgin will only close on exit? Thx in advance for any help...

I was wondering the same thing. ^^

---

### Post by d5j9 on 2010-03-16
You need to go to tools > preferences > show system tray icons and set it to always.

---

