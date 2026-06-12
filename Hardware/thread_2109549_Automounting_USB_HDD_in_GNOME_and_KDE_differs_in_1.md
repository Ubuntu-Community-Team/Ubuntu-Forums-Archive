---
title: "Automounting USB HDD in GNOME and KDE differs in 12.10"
date: 2013-01-27
forum: Hardware
---

### Post by ssrublev on 2013-01-27
I have an external HDD connected to PC's USB which is connected permanently. I want to use it as a regular permanent drive when I log in both into KDE and GNOME (or rather MATE) in 12.10 (for torrents, music etc).

But KDE mounts it as /media/Expansion Drive/
and GNOME (MATE) as /media/<username>/Expansion Drive/

So that it's different every time and same torrent clients and media players can't handle the files simultaneously. Please help me to mount it at the same mount point each time. When I try to include this in fstab it conflicts with automount.

**Update**: not GNOME but UNITY!!! So sorry!!!

---

### Post by ssrublev on 2013-01-28
Well, I've got it. The thing is in file managers. Direct mount /media/drive is Dolphin's and /media/%name%/drive stands by Nautilus (Caja in MATE, Nautilus fork). I had to disable startup mount in KDE and include Nautilus in KDE autostart (with --no-desktop argument) — so it mounts the right way with system start. I have a Nautilus popup at startup though, but well I'll be closing it. But media players and torrent clients are able to keep permanent libraries now. Worked for openSUSE as well.

---

