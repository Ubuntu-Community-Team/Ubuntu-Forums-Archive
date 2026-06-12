---
title: "Getting cron to work"
date: 2005-12-06
forum: General Help
---

### Post by dmh-bidlah on 2005-12-06
Hi.
Previously when using KDE I had this neat little script that would start playing in the morning, effectively waking me up. Now that I have Ubuntu I want to implement the same thing again, but using MPD(Music Player Daemon).
I figured cron was the best way to go. So i just typed
```
crontab -e
```
to a terminal and made it look like this:
```
15 7 * * * joosep mpc play
```
The thing is it wouldn't work. Is there some trick involved or am I just missing something?
Thanks

---

### Post by BIS on 2005-12-06
I am guessing you need to put in the full path to mpc

---

### Post by henriquemaia on 2005-12-06
[QUOTE=dmh-bidlah]Hi.
Previously when using KDE I had this neat little script that would start playing in the morning, effectively waking me up. Now that I have Ubuntu I want to implement the same thing again, but using MPD(Music Player Daemon).
I figured cron was the best way to go. So i just typed
```
crontab -e
```
to a terminal and made it look like this:
```
15 7 * * * joosep mpc play
```
The thing is it wouldn't work. Is there some trick involved or am I just missing something?
Thanks[/QUOTE]

I guess this isn't much help, but as far as my experience is concerned, cron on ubuntu can't run X programs. I have tried the same thing over and over again without success.

I now use kalarm deamon to achieve this (even though I rather prefer to use cron).

---

### Post by dmh-bidlah on 2005-12-06
[QUOTE=henriquemaia]I guess this isn't much help, but as far as my experience is concerned, cron on ubuntu can't run X programs.[/QUOTE]
It is quite logical actually, since it doesn't know where to run it and can't find an Xserver. But mpc is a commandline program.

Using the full path didn't work.

Actually I haven't got anything to run from cron so far, not even echo.
Thanks for the replies so far, hope to fix it by today ;)

---

### Post by henriquemaia on 2005-12-07
[QUOTE=dmh-bidlah]It is quite logical actually, since it doesn't know where to run it and can't find an Xserver. But mpc is a commandline program.

Using the full path didn't work.

Actually I haven't got anything to run from cron so far, not even echo.
Thanks for the replies so far, hope to fix it by today ;)[/QUOTE]

But even when I do specify the X server to use, nothing happens (on X).

As a test, I have added this to crontab:

```
*/1 * * * * henriquemaia /usr/bin/gcalctool :0 >> /home/henriquemaia/logcron.txt 2>&1
```

On the log, I get:

```
(gcalctool:9471): Gtk-WARNING **: cannot open display:
```

But when I run the same command from another tty, the command runs fine.

Any ideas how to make cron accept a command running on a specific X?

ps: dmh-bidlah, cron actually does something, as you can see by the writing on the log. So you must have a different problem. Have you added your user to cron.allow?

---

