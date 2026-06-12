---
title: "Cron won't wake me up"
date: 2008-07-25
forum: General Help
---

### Post by crosswalker21 on 2008-07-25
Hey everbody!

I'm attempting to schedule a flac file to play at a certain time in the morning for use as an alarm clock  Unfortunately, cron has other plans.  I used crontab -e to run /home/joe/.alarm at a certain time (just a couple minutes in the future, for testing purposes, for instance 20 22 * * * /home/joe/.alarm if I was trying it at 10:20pm) and it doesn't do anything. I've run chmod 700 and chmod +x on .alarm (contents underneath).  If I run /home/joe/.alarm from the terminal Totem opens and the file starts playing.  Is there something I'm doing wrong?

Contents of .alarm
```
#!/bin/sh
totem /home/joe/Music/Jeff\ Wahl/Meditative\ Guitar/12-The\ First\ Day-Jeff\ Wahl.flac
```

Thanks in advance for any help!

---

### Post by SOULRiDER on 2008-07-25
Im not sure but I believe it has to be restarted.

Ive had to do this ebfore and I used Exaile, it has a ncie alarm clock plugin :(

---

### Post by Herman on 2008-07-26
:) We can easily configure the Calendar in Evolution Email in Ubuntu to do things like that from GUI, [Memos, Tasks and Calendar Appointments]("http://users.bigpond.net.au/hermanzone/p5.htm#Memos_Tasks_and_Calendar_Appointments").

I used to use crontab too, before I found it was easier to do it with Evolution.
The problem you're having could possibly be that the program you're trying to run from cron is a GUI program.
 Thanks to henriquemaia for this how-to: [crontab: How to run GUI programs with cron]("http://www.ubuntuforums.org/showthread.php?t=185993")

for instance,
```
crontab -e
```...and paste in a line something like this one,
```
20 22 * * * [COLOR=Sienna]**export DISPLAY=:0 &&**[/COLOR] /usr/bin/totem /home/joe/Music/Jeff\ Wahl/Meditative\ Guitar/12-The\ First\ Day-Jeff\ Wahl.flac
```Here's one of my own crontab entries,
```
5 4 * * * **[COLOR=Sienna]export DISPLAY=:0 &&[/COLOR]** /usr/bin/totem /home/herman/Music/*
```:) Regards, Herman

---

### Post by crosswalker21 on 2008-07-26
Thank you very much Herman!

Works like a charm!

I've been aware of the evolution scheduling operations for a while, but I wanted to give cron a shot (mostly as an experiment in unix).

My new, working, crontab is
```
0 6 * * * export DISPLAY=:0 && /home/joe/.alarm
```

---

