---
title: "Evolution will not start"
date: 2008-09-12
forum: General Help
---

### Post by eudemus on 2008-09-12
Hi,
I'm running Kubuntu Hardy (KDE 3.5 version), and am going back to using evolution mainly for calendar. It can sync with my palm better than other apps.

However, now I am having difficulty getting Evolution to load at all. It has loaded once or twice, since I installed it a few days back, but usually when I choose it from the menu, it starts to load, seems to keep trying for a while and then nothing further happens.

A few days back, having done this a few times, abandoning the attempt, and working on something else, I found ages later that I had a couple of Evolution sessiosn finally open.

But mostly it doesn't open at all.

Is there some difficulty perhpas between Evolution and KDE???? There shouldn't be.

Any ideas?
Thanks in advance,
Eudemus

---

### Post by ajmorris on 2008-09-12
hi there,
try running evolution from a terminal, and post the output here.

AJ

---

### Post by eudemus on 2008-09-12
Here's the output:

START OF PASTE

** (evolution:6503): WARNING **: couldn't connect to dbus session bus: Failed to execute dbus-launch to autolaunch D-Bus session

** (evolution:6503): WARNING **: couldn't connect to dbus session bus: Failed to execute dbus-launch to autolaunch D-Bus session

** (evolution:6503): WARNING **: couldn't connect to dbus session bus: Failed to execute dbus-launch to autolaunch D-Bus session

<snip - a load of blank lines>

error : unterminated entity reference         Esslnet
error : unterminated entity reference  Opensync & Synce


END OF PASTE

Just to clarify, "Esslnet" and "Opensync and Synce" are names of folders in  my Exchange inbox which it looks like Evolution is trying to access (I don't need it to do this, but am not sure how to stop it trying). Presumably this is stuff leftover in some config file from when I have previously used evolution and tried to use it to access my work exchange inbox.

Anyway, there's the output. Any suggestions?

Best, Eudemus

p.s. while I've been typing, Evolution has opened...

---

### Post by eudemus on 2008-09-12
OK. Having got into Evolution, seen that I still had the exchange account active (and hence presumably it was trying to connect at start up), I deactivated that mail account.

Bingo! No problems starting up now.

Thanks, AJ.

All the best, Eudemus.

---

