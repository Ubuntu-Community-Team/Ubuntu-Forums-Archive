---
title: "[SOLVED] Cron doesn't like .jar files"
date: 2008-08-05
forum: General Help
---

### Post by ownaginatious on 2008-08-05
For some reason, I cannot for the life of me get cron to run a certain .jar file I have at a set time. It can run everything else fine, just not .jar files it seems. It's executing this .jar file directly, and not through a script. The reason I made the jar is to do some basic cleanup of a log file that gets created periodically by w/e the file syncing program I have is (I think rsync...)

Can anybody help me out? This is driving me insane...

Any help would be GREATLY appreciated.

---

### Post by apmcd47 on 2008-08-05
Can you show us the contents of this crontab entry? My guess is that you are trying to run the .jar file directly when you should be invoking java. But I don't program in java and have no idea how .jar files should be run.

Andrew

---

### Post by ownaginatious on 2008-08-05
No, I'm using the java command that you have to insert beforehand. It works when I put that command directly into the terminal and run it myself, but not when it goes through cron... weird. I'll post my crontab when I get home later today.

---

### Post by apmcd47 on 2008-08-05
Okay, perhaps java isn't in cron's path. Try the full path to java in your crontab entry, and possibly the full path of your .jar file.

Andrew

---

### Post by ibuclaw on 2008-08-05
Is it a GUI app you are trying to run?
If so, you have to specify with DISPLAY you want to run the job on, else it won't start, since the runlevel cronjobs run at don't have access to X.

Regards
Iain

---

### Post by ownaginatious on 2008-08-05
Nope, it's not a GUI application. It's not interactive at all, just basically creates an HTML page based on some information in a text file.

---

### Post by ownaginatious on 2008-08-09
[COLOR="Magenta"]# m h  dom mon dow   command
30 10 * * 1 java -jar /home/administrator/CreateLog.jar
[/COLOR]

The above is my crontab. Why isn't it running?

---

### Post by mikjp on 2008-08-09
> **ownaginatious said:**
> [COLOR="Magenta"]# m h  dom mon dow   command
30 10 * * 1 java -jar /home/administrator/CreateLog.jar
[/COLOR]

The above is my crontab. Why isn't it running?

Probably java is not in the path. Try adding the complete path to java (use: which java).

In openSUSE it would be

[FONT="Courier New"]/usr/bin/java -jar /home/administrator/CreateLog.jar[/FONT]

Greetings,

mikko

---

### Post by ownaginatious on 2008-08-09
> **mikjp said:**
> Probably java is not in the path. Try adding the complete path to java (use: which java).

In openSUSE it would be

[FONT="Courier New"]/usr/bin/java -jar /home/administrator/CreateLog.jar[/FONT]

Greetings,

mikko

That unfortunately appears to have had no effect :(

---

### Post by ModelM on 2008-08-09
Try creating a shell script containing your task commands, & having cron call the shell script - so if your script was named "do.my.job" your crontab would look like:

```
# m h dom mon dow command
30 10 * * 1 /home/my_directory/binfiles/do.my.job

```

---

### Post by ownaginatious on 2008-08-10
Okay guys, I got it all working properly now. It turns out that since I had been running these commands from the root's crontab, rather than my crontab, the paths were getting all screwed up, resulting in failure. I got it all to work now though by moving all the files executed/read to the /root directory from my /home/administrator folder.

Thanks for all your help everyone, I really appreciate it.

---

