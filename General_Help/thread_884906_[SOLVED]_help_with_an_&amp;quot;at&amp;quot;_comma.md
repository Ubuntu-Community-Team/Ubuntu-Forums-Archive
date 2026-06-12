---
title: "[SOLVED] help with an &amp;quot;at&amp;quot; command"
date: 2008-08-09
forum: General Help
---

### Post by Comandos on 2008-08-09
Hey,
I've been trying to run this "at" command so it'll play music for 10 seconds then stop Mplayer, but Mplayer won't stop. Can one of the experts here help me? I ran the command seperetly and they work, but the at command plays the music but never stops.

> gal@gal-laptop:~$ at 10:30 AM
warning: commands will be executed using /bin/sh
at> mplayer -playlist "/home/gal/Desktop/Gal-backup/playlist.txt"
at> sleep 10
at> kill `ps -C mplayer -o pid=`
at> <EOT>
job 8 at Sat Aug  9 10:30:00 2008

---

### Post by Sycron on 2008-08-09
You may try **killall mplayer** but i'm not sure.

---

### Post by Comandos on 2008-08-09
well the command works I know for a fact but the "at" command seems to ignore it...

---

### Post by mikjp on 2008-08-09
Would adding & at the end of the line with mplayer do the trick? 

I think your version plays first the playlist, then waits 10 seconds, and then tries to kill the app.

Greetings,

m

---

### Post by sisco311 on 2008-08-09
to play the first 10 seconds of a file use:
```
mplayer -endpos 10 ...
```

---

### Post by Comandos on 2008-08-09
well the 10 secs thing's only an expirament. I want to play the first 15 minuets of the playlist

---

### Post by Sycron on 2008-08-09
Maybe will work if the file is a playlist ... you must try it ...

---

### Post by sisco311 on 2008-08-09
```
mplayer -endpos 00:15:00 filename
```the format is hh:mm:ss

edit:
i have no short media files to test if it works with playlist

---

### Post by Comandos on 2008-08-09
I did. It seems to play the first 10 seconds of the first file than go to the next one...

EDIT: the & thing works guys. Thanks for all of your help, I appreciate it.

---

### Post by mali2297 on 2008-08-09
Create a script that contains
```

#!/bin/sh

mplayer -playlist "/home/gal/Desktop/Gal-backup/playlist.txt" &
sleep 10
pkill mplayer

```
and execute it through *at*.

Alternatively, set up two *at* jobs: one that starts mplayer and another one which stops it.

EDIT: Oh, I guess I'm late... Nevermind.

---

