---
title: "[SOLVED] cron jobs"
date: 2008-09-15
forum: General Help
---

### Post by baudday on 2008-09-15
I'm having trouble understand how cron jobs work. I'm trying to have an hourly job that copies the contents of wwwboard.html to backup.txt. I thought I could just put the following in a .sh file and save it in /etc/cron.hourly/ but it doesn't seem to be running. Any help?

wwwboard.sh:
```
cd /var/www/wwwboard/
cp wwwboard.html backup.txt
```

---

### Post by Peter09 on 2008-09-15
Have you made it executable?

do
```
ls -alg
```


the file should have the x bit set for root.

---

### Post by baudday on 2008-09-15
-rwxr-xr-x   1 root    49 2008-09-15 10:10 wwwboard.sh
Not sure what you mean by the x bit. but that's the file

---

### Post by Peter09 on 2008-09-15
Ok.

How do you know that the script has not run?

Has it run but not done what you expect?

---

### Post by baudday on 2008-09-15
this could be true. But I don't see why. If it's running as root it should have done what I wrote in there. Do you have a suggestion as to what I could change?

---

### Post by unutbu on 2008-09-15
Edit wwwboard.sh to look like this:
```

#!/bin/sh
cd /var/www/wwwboard/
cp wwwboard.html backup.txt

```
That might be enough to get your cron job working.

To test your cron without having to wait an hour, type
```

sudo -i                   # Enter root shell
EDITOR=gedit crontab -e   # Edit root's personal crontab
```

and add this
```

00 13 * * *  /full/path/to/wwwboard.sh

```
Save and Exit.

Cron should then try to execute wwwboard.sh at 13:00.

You can check that cron at least tried to execute your script by checking /var/log/syslog:
```

watch -n 1 tail -n 10 /var/log/syslog
```

---

### Post by iponeverything on 2008-09-15
Make sure that the last line ends with a newline.

---

### Post by baudday on 2008-09-15
Two things, when I enter 
```
sudo -i
EDITOR=gedit crontab -e
```
I get 
```
/bin/sh: gedit: not found
crontab: "gedit" exited with status 127

```

And where do I add 
```

00 13 * * *  /full/path/to/wwwboard.sh

```

---

### Post by unutbu on 2008-09-15
Hm. Are you running Ubuntu? I think gedit is one of the editors that is installed by default. If you use Kubuntu, there might be a different editor installed (kate?).

As a normal user, what happens when you type gedit?

Anyway, that is probably an unrelated issue.

You can also just type
```

sudo -i
crontab -e
```

You will get the default editor (probably nano). It works fine; it's just not as graphical.

A text editing window will pop up, and you can add the line```


20 13 * * *  /full/path/to/wwwboard.sh

```
there. Edit the time as necessary. The above will execute at 13:20. For nano, press Ctrl-X to save and exit. Its menu bar writes ^X to mean Ctrl-X.

---

### Post by baudday on 2008-09-15
Sep 15 12:25:01 ellishome-main /USR/SBIN/CRON[18671]: (root) CMD (/etc/cron.hourly/wwwboard.sh)

Looks like it ran, but it didn't do what it was supposed to.

---

### Post by baudday on 2008-09-15
Okay, my bad, it did exactly what I told it to, I just put the wrong filename. Thanks a lot for the help

---

### Post by baudday on 2008-09-15
real quick, can i remove that line from crontab? since the file is in cron.hourly will it automatically execute every hour?

---

### Post by unutbu on 2008-09-15
Glad you solved the problem.

Yes, you can simply delete that line from crontab and cron will stop executing it.

---

### Post by baudday on 2008-09-15
and it'll still execute hourly?

---

### Post by unutbu on 2008-09-15
You betcha.

There are many places to set cron jobs.
Each individual has their own crontab which they can edit by running
```

crontab -e
```
root also has a personal crontab.
Then there is /etc/crontab, which is separate from the personal crontabs and has an additional field for specifying the user.

If you look inside /etc/crontab you'll see the code which makes /etc/cron.hourly work.


Type 
```

man 5 crontab  # To read about the format of the crontab line 
man crontab    # For general info on crontab
```

---

### Post by baudday on 2008-09-15
looks like it's not running with cron.hourly. I didn't remove that line from crontab yet.

---

### Post by baudday on 2008-09-15
well, i ended up just modifying the original line to make it execute every hour, and that seems to be working.

---

### Post by unutbu on 2008-09-15
Oh yes...
Scripts in /etc/cron.hourly (or any script called through run-parts) must have a name that does not end in .sh. If you change the name of your script from 
wwwboard.sh to wwwboard, I think it might actually run.

See [http://gnuru.org/article/952/cron-run-parts-script-names](http://gnuru.org/article/952/cron-run-parts-script-names)

---

