---
title: "Sony Vaio laptop diagnostic help"
date: 2008-08-31
forum: Hardware
---

### Post by John_T on 2008-08-31
I've just recently installed 8.04 from a live CD.  The install went well and the machine rebooted and ran first time.  So far so good.

However, it seems to almost lock up, on a regular basis.  When I say "almost", I mean that I can't select anything and all processing seems to have stopped, although the mouse touch pad is still working, and the mouse pointer is movable and quite responsive.

Using the command line I've managed to get all of the standard updates installed,as well as the non-free drivers for the video card.  I've attempted to install updated video drivers using EnvyNG, but never gotten through before the lockup occurs.

My questions are:
[LIST=1]
[*]Where should I look (log files etc) to get a better idea of what's causing the lockup?
[*]Has anyone else seen this type of semi-lockup?
[/LIST]

Notes:
[LIST]
[*]Sony Vaio PCG-9H3P, Athlon based machine. 
[*]I've run memory check overnight, with no errors found.
[*]I've run a slew of disk checks, the HD seems to be in good condition.
[*]Any processes (downloads etc) stop once it's locked up, but the mouse itself is still controllable and quite responsive.
[*]Lockups occur anytime from sever seconds after login and the desktop appears, to a few minutes later, but never more then 5 minutes or so in my experience thus far.
[/LIST]

Any and all help would be much appreciated.

---

### Post by IntuitiveNipple on 2008-08-31
John, does it lock up if you don't log-in?

Also, if you stop Gnome and use the console terminal does it lock up?

To test this latter question, close all applications and log-out of Gnome. When at the log-in screen press Ctrl+Alt+F1 to take you the console on TTY1 (TeleTYpe 1), log-in and then do:
code]
sudo /etc/init.d/gdm stop

tail -f /var/log/kern.log
[/code]
and watch. The "-f" causes tail to monitor the log file and show all new entries added to it so you can effectively watch 'live' and maybe get a clue as to what is causing the lock-up, if it happens outside of X, and also causes some kind of log event.

to restart Gnome do:
```

sudo /etc/init.d/gdm start

```

---

