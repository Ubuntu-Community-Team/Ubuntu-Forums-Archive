---
title: "HOWTO use Synaptic in KDE with update-notifier-kde"
date: 2009-08-20
forum: Installation &amp; Upgrades
---

### Post by eudemus on 2009-08-20
This took me a while to solve, so thought I'd post on it.

Synaptic seems to me to do a better overall job than the KDE tools proposed these days (KPackagekit, Adept, etc.). Especially, you can prevent your updates from trying to upgrade a program where you have deliberately kept a previous version - as one might wish to do with, say, Kile or Amarok.

But how do you get the update notifier to sit in the system tray and send you to Synaptic to review and apply the updates.

The answer is here (you need to scroll down):
[http://kubuntuforums.net/forums/index.php?topic=3103514.0](http://kubuntuforums.net/forums/index.php?topic=3103514.0)

I tried and failed to get update-notifier (the Gnome version) to appear in the KDE system tray. What the above link tells you how to do is to get update-notifier-kde to point to Synaptic.

And it was pretty easy in the end.
Cheers, Eudemus


in case it's maybe more convenient, here's the relevant bit from the link above:

[INDENT]The update-notifier-kde (update-notifier-kde.py) is a python script. It is in /usr/share/python-support/update-notifier-kde.


Messing with the defaults (remember the backup before you edit ;))

/usr/share/python-support/update-notifier-kde/update-notifier-kde.py has a line (201):

```
KProcess.startDetached("kcmshell4", ["kpk_update"])

```

Change it to:

```
KProcess.startDetached("kdesudo", ["synaptic --upgrade-mode"])

```

After log out and log in Synaptic package manager will start when "update" icon is pressed.
[/INDENT]

---

