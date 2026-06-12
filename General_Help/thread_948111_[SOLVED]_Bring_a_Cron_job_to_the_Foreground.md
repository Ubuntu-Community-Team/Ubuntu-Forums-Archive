---
title: "[SOLVED] Bring a Cron job to the Foreground"
date: 2008-10-14
forum: General Help
---

### Post by Altay_H on 2008-10-14
I use cron to launch mplayer and often end up wanting to skip to the next song. Unfortunately, because there's no terminal with mplayer in its foreground, I have no way of controlling mplayer except for "killall mplayer." Is there a way to bring a cron job to the foreground of a terminal window?

---

### Post by DagMan on 2008-10-14
Is the problem that you don't have a gui?  If not you can make your cron job launch gnome-terminal or xterm with mplayer.

xterm -e mplayer some-file.mp3

gnome-terminal -x "mplayer some-file.mp3"

something like the above, though you'de want to put them in a script or provide the full path to the programs.


If it's a server install without a gui, there's the "at" command, which I don't know how to use but it looked useful to others.

---

### Post by jpkotta on 2008-10-15
Try this:
```
screen -d -m mplayer file.ext
```

screen is a program that wedges itself between an actual terminal emulator (e.g. xterm) and a command (e.g. mplayer).  You can use it for all sorts of useful things, but the main thing here is that you can reattach to already running but "detached (from the terminal)" instances of screen.

List running instances of screen.
```
screen -ls
```

Reattach to the first running instance, if any.
```
screen -r
```

I didn't test with a cron job.

---

### Post by Altay_H on 2008-10-15
> **DagMan said:**
> Is the problem that you don't have a gui?  If not you can make your cron job launch gnome-terminal or xterm with mplayer.
No, I'd prefer to launch mplayer without a gui. Thanks anyway.


> **jpkotta said:**
> screen is a program that wedges itself between an actual terminal emulator (e.g. xterm) and a command (e.g. mplayer).  You can use it for all sorts of useful things, but the main thing here is that you can reattach to already running but "detached (from the terminal)" instances of screen.
screen was exactly what I needed. Thanks!

---

