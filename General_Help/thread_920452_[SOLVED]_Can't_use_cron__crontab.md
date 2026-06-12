---
title: "[SOLVED] Can't use cron / crontab"
date: 2008-09-15
forum: General Help
---

### Post by Xavier Oddmon on 2008-09-15
Hello. I have done some searching, but have yet to find a solution to this bothersome problem:
I have a script that checks my email, and blinks the scroll lock / caps lock key depending on wether I have mail in my two accounts. (I found this script [here]("http://ubuntuforums.org/showthread.php?t=812656") and modified it to my liking.) 

It runs fine, for example, if I put into a terminal /home/chris/scripts/checkGmail, the LEDs blink (assuming I have mail).

I then created a crontab entry 
```
*/5 * * * * /home/chris/scripts/checkGmail
```
Didn't work. So, after some testing, my crontab now looks like this:
```
* * * * * nautilus
```
I hoped that this would open nautilus every minute, just so i can see wether it works. It doesn't. I also tried putting my scripts in cron.hourly, but it didn't run there either. I have an empty cron.deny file that i created, but this didn't work before or after I created it. What am I doing wrong?

---

### Post by jigsaws on 2008-09-15
You can't do this way. Cron jobs have no connection to "context" (terminal, etc) you editing cron. If you want to test cron try rather:
* * * * * echo `date` >> /tmp/test.txt

---

### Post by Oldsoldier2003 on 2008-09-15
> **Xavier Oddmon said:**
> Hello. I have done some searching, but have yet to find a solution to this bothersome problem:
I have a script that checks my email, and blinks the scroll lock / caps lock key depending on wether I have mail in my two accounts. (I found this script [here]("http://ubuntuforums.org/showthread.php?t=812656") and modified it to my liking.) 

It runs fine, for example, if I put into a terminal /home/chris/scripts/checkGmail, the LEDs blink (assuming I have mail).

I then created a crontab entry 
```
*/5 * * * * /home/chris/scripts/checkGmail
```
Didn't work. So, after some testing, my crontab now looks like this:
```
* * * * * nautilus
```
I hoped that this would open nautilus every minute, just so i can see wether it works. It doesn't. I also tried putting my scripts in cron.hourly, but it didn't run there either. I have an empty cron.deny file that i created, but this didn't work before or after I created it. What am I doing wrong?
for a graphical application you must specify the display. also for cron it is always best to use the full path. You can use "which" to get the path
```
chuck@apocalypse:~$ which nautilus
/usr/bin/nautilus

```
so the cronjob would look like this
```
* * * * * DISPLAY=:0 /usr/bin nautilus
```

---

### Post by Xavier Oddmon on 2008-09-26
Alright, this all makes sense. Thanks. The script is running just fine, I just can't hear anything. The script uses the espeak command to say that I have email. However, this fails if I've got music playing. So, I changed it to do the following:

```
espeak -w /home/chris/scripts/announcement.wav "$mailsa new emails in main account.";
mplayer /home/chris/scripts/announcement.wav;
rm /home/chris/scripts/announcement.wav;

```

Now I hear nothing. my crontab is as follows:

```
*/5 * * * * DISPLAY=:0 /home/chris/scripts/checkGmail.sh
```

Do I have to do something to get mplayer to play sound to this display (?), or is there something I can do to espeak to make it play over my other audio apps?

---

### Post by jigsaws on 2008-09-28
But what when you turn off X? (ie. in runlevel 3)?
:-)

I'm not sure that cron is the best way. Years ago there was something very popular - xbiff. Maybe you can go that way?

---

