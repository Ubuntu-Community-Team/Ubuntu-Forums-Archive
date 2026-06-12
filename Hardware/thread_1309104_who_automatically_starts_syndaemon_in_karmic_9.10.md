---
title: "who automatically starts syndaemon in karmic 9.10?"
date: 2009-11-01
forum: Hardware
---

### Post by frprovis on 2009-11-01
I am NOT interested in how to start syndaemon from the command line. The man pages are very clear about this.

I am NOT interested in how to automatically start programs in general using System'Startup Applications. The help is very clear about this.

I am solely interested in what part of the system is AUTOMATICALLY starting syndaemon under the standard installation of Ubuntu 9.10 (Karmic Koala). I want to know because I don't like the default of a 2second wait time and would prefer to modify the automatic startup to specify 5seconds. I repeat. I want to know WHERE syndaemon is currently being started, not how to start it. 

Thanks,

---

### Post by lunch on 2009-11-01
It's hardcoded to 0.5 seconds:

[http://git.gnome.org/cgit/gnome-settings-daemon/tree/plugins/mouse/gsd-mouse-manager.c?id=46cfbb45bac09fd86f13a1995a4b4b2742b39c25#n498](http://git.gnome.org/cgit/gnome-settings-daemon/tree/plugins/mouse/gsd-mouse-manager.c?id=46cfbb45bac09fd86f13a1995a4b4b2742b39c25#n498)

You have to kill syndaemon and restart it with the new settings.

---

### Post by stroyan on 2009-11-01
It is actually started by gnome-settings-daemon.
But you can disable that copy of syndaemon from being started.
Use the "System" menu.
Choose "Preferences" and "Mouse".
Switch to the "Touchpad" tab.
Uncheck "Disable touchpad while typing".

---

### Post by frprovis on 2009-11-01
Thanks very much for the quick replies.:p

I don't understand why gnome is using a hard-coded .5s default rather than letting the user specify the delay time. .5secs is way too short for me. But I'll go ahead and change the mouse settings so syndaemon is not started automatically. But that brings up another question. What is the standard way in linux for the user to run a script at logon time, so that I can start up syndaemon with the 5 second delay? I'm a complete newbie to Ubuntu, though very impressed and happy with it on my new Dell Mini10v (other than not having support for the Broadcom 4322 wireless card builtin, which means I needed a wired connection to install, which might be a problem in the future as I might have to cancel my cable service due to budget problems.).

Edit: Nevermind the question about how to run scripts. I'll use that Startup Applications applet.

---

