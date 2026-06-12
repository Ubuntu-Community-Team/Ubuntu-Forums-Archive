---
title: "Cron running but jobs not executing?"
date: 2008-09-10
forum: General Help
---

### Post by WindPower on 2008-09-10
Hello,

I'm trying to set up a basic cron job that simply opens two web pages, each day at 20:30.
So I edited my crontab to the following:
```
30 20 * * * /media/Data/Tasks/2030.py
```
/media/Data/Tasks/2030.py is a script which contains the following:
```
#!/usr/bin/env python
import webbrowser

webbrowser.open_new_tab('http://www.somepage.com')
webbrowser.open_new_tab('http://www.someotherpage.com')
```Running the script manually works just fine, but cron seems not to do anything, even if I change the line to
```
* * * * * /media/Data/Tasks/2030.py
```so that it runs every minute.
I tried using gnome-schedule to set up my crontab, same results. "ps -e | grep cron" and the System Monitor both show that cron is running indeed. "sudo /etc/init.d/cron restart" says "* Restarting periodic command scheduler crond                           [ OK ]", so I'm assuming there's no problem with cron. Is something wrong with my Python script, then?

---

### Post by aloshbennett on 2008-09-11
The sha-bang line (#!) doesnt look okay to me.
How did you run this script manually?
> ./2030.py
or
> python 2030.py
?

---

### Post by kpkeerthi on 2008-09-11
I guess, you need to tell the cron which display to use when launching GUI apps with it.

Change it to something like below, restart the cron daemon and see if it helps:
```

* * * * * env DISPLAY=:0. /media/Data/Tasks/2030.py

```

**env DISPLAY=:0.** indicates 'use current display'

---

### Post by WindPower on 2008-09-11
aloshbennett, both ways work and do the same thing, I'm positive about the shebang.

kpkeerthi's solution didn't work, but that's because of the extra dot after the 0 ("env DISPLAY=:0_**[color="red"].[/color]**_ /media/Data/Tasks/2030.py"). Removing it solved the problem. Thanks! :KS

---

