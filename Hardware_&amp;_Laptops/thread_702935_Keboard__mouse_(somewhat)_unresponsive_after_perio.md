---
title: "Keboard / mouse (somewhat) unresponsive after periods of no input"
date: 2008-02-20
forum: Hardware &amp; Laptops
---

### Post by linzer on 2008-02-20
I'm in need of help troubleshooting a keyboard / mouse problem that exists in i386 Gutsy for me.  This did not exist in Dapper.

Description of problem:
After lengthy periods of inactivity for the mouse and keyboard (overnight, while at work, etc.) the keyboard and mouse clicks do not appear to be responsive on Gutsy for me.  HOWEVER, the mouse cursor does move around on the screen.  Eventually clicking/keyboard catch up with display.  The amount of time required to get system responsive appears related to the amount of inactive time.  Recently I was out of town for a couple of days (with the computer running but basically inactive for the keyboard/mouse) and I waited 15 minutes without the keyboard/mouse becoming responsive.  Overnight periods of inactivity result in roughly 5 minute wait times for the keyboard/mouse to snap back to life.

For very long wait times, I find it easier to ssh into the box and kill x-session-manager.  This snaps the system back to life without issue.  Reviewing "top" while sshed into the box reveals no processes taking up a bunch of memory or CPU cycles.

Steps taken for troubleshooting without any impact.

1) Turn off remote desktop connections into the box.
2) Turn off power management

Again, these problems did not exist for me in Dapper.  When I installed Gutsy I performed a new install, not an upgrade.

Differences between Dapper and Gutsy w.r.t. video / desktop items--Dapper I ran Kiba with Gutsy I'm running AWN.  Dapper I ran Beryl with Gutsy I'm running Compiz (whatever is installed by default).  [edit]In Dapper I ran gdesklets with Gutsy I'm running Screenlets.[/edit]

Seeing as my Dapper build isn't around any longer I'm not sure what the most recent kernel/restricted nVidia drivers I was running but with Gutsy I've also got the most recent packages.

Can you point me to any logs or elsewhere I could look at that might help troubleshoot.

Much appreciated.

---

### Post by linzer on 2008-02-24
Bump

---

