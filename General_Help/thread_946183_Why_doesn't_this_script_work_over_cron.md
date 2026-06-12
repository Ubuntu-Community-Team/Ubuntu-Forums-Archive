---
title: "Why doesn't this script work over cron"
date: 2008-10-13
forum: General Help
---

### Post by mlissner on 2008-10-13
The script below works well when called. It pulls the IP address of the computer, puts it in a file at line 236, and then transfers that file to another computer. 

```
#!/bin/bash
# A script to send my IP address to the backup server

IP=`ifconfig wlan0 | grep "inet addr" | cut -d ":" -f 2 | cut -d " " -f 1`

sed "236s/TARGET/$IP/" rsnapshotTarget.conf  > rsnapshotOpalUpdated.conf

scp rsnapshotOpalUpdated.conf mlissner@192.168.1.132:/home/mlissner/Backups/conf/rsnapshotOpal2.conf

exit 0
```When I run this from a cron job though, the file that results on the remote machine is empty; it has no contents. 

Any theories on why a file transfer would work, but not via a cron job? I also tried this as root...that also fails.

---

### Post by fsmithred on 2008-10-14
Two thoughts:
I think you need to use the full path to the files in the script.
Make sure you have a blank line at the end of your crontab. 

From man crontab:

BUGS
       Although cron requires that each entry in a crontab end in a newline character,  neither  the  crontab
       command nor the cron daemon will detect this error. Instead, the crontab will appear to load normally.
       However, the command will never run. The best choice is to ensure that your crontab has a  blank  line
       at the end.

---

### Post by mlissner on 2008-10-14
Brilliant! Of course cron doesn't know where to find files. Duh. I've changed the script as of now, but we won't have results until later tonight when it runs. Will keep this thread posted.

---

### Post by mlissner on 2008-10-15
Well, we've made progress, because the proper file is getting sent now, but not the value of the IP variable isn't getting used in the sed line. 

I'm guessing cron can't find it even though it's in the scope of the script? My guess is I need to export the variable or something. Any thoughts? I'm clearly more than a little rusty on my bash skills.

---

### Post by fsmithred on 2008-10-15
Well, I'm no script wizard, so I don't know if I can help. I played with it, and I can confirm that it works fine from command line, but as a root crontab, the IP number doesn't get copied to the file on the local machine - there's a blank space where it should be. Then that file gets copied to the remote machine, still missing the IP number, of course.

---

### Post by mlissner on 2008-10-15
Yep. That's pretty much exactly what it's doing here too...it looks like I may have to play with this some more before it will work.

---

### Post by mlissner on 2008-10-17
OK - I've played with the script some more, and frustratingly, it still doesn't work as it should. It seems that it has problems passing the IP variable to sed, though I'm baffled as to why. 

Any ideas out there?

---

### Post by fsmithred on 2008-10-18
Got it!

I just tried adding the script to /etc/cron.hourly and restarted cron, and it works that way.

Or, if you want to run it as a crontab, add a line to export root's PATH. I don't know if this is the best way to do it, but it works.
```
#!/bin/bash
# A script to send my IP address to the backup server

export PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
IP=`ifconfig wlan0 | grep "inet addr" | cut -d ":" -f 2 | cut -d " " -f 1`

sed "236s/TARGET/$IP/" /path/to/rsnapshotTarget.conf  > /path/to/rsnapshotOpalUpdated.conf

scp /path/to/rsnapshotOpalUpdated.conf mlissner@192.168.1.132:/home/mlissner/Backups/conf/rsnapshotOpal2.conf

exit 0
```

---

### Post by mlissner on 2008-10-18
Like a charm. I also added a little bit to it to make it more informative. Here's the latest:```
#!/bin/bash
# A script to send my IP address to the backup server

export PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
IP=`ifconfig wlan0 | grep "inet addr" | cut -d ":" -f 2 | cut -d " " -f 1`

sed "236s/TARGET/$IP/" /home/mlissner/bin/rsnapshotTarget.conf  > /home/mlissner/bin/rsnapshotOpalUpdated.conf

scp /home/mlissner/bin/rsnapshotOpalUpdated.conf mlissner@192.168.1.132:/home/mlissner/Backups/conf/rsnapshotOpal2.conf

if [ $? = 0 ]
then
  notify-send -t 3000 "Backup Proceeding on IP $IP"
else
  notify-send -t 3000 "No backup at this time"
fi

exit 0

```

---

### Post by cicatrix1 on 2008-10-18
Right.  This means that one of the commands called is an alias, or something that was dependent on the user's environment.  To be safe, anytime you call an outside file from a script, provide the full pathname.  This also goes for things like ifconfig (i.e. use /sbin/ifconfig) and cut.

--Matt

---

