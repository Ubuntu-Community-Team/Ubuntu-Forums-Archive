---
title: "crontab jobs not executing..."
date: 2008-07-27
forum: General Help
---

### Post by Mia_tech on 2008-07-27
I have this entries in my /etc/crontab file, and they are not executing the firstone
```
05 00	* * 4	root	/home/jorge/task/homebackup.sh > /var/log/homebackup.log
```

it is expected to make a backup of my home directory on Thursdays at five min past midnight, but it's not doing anything, and logs are empty.... yes the homebackup.sh has execute permisions

and the second one
```
00 00 	* * 1-5	root	clamscan -ri --log=/var/log/clamscan.log --move=/tmp/virus /
``` 

my antivirus which I want it to run at midnight from Mondays to Fridays...

could someone check if they are correct


thanks

---

### Post by Potatoj316 on 2008-07-28
dont have the > logfile in your crontab entry.  i think its suposed to work but its simpler if you just put it in the script your executing.  Also try 
```
crontab -l
```
to make sure these lines are actually "seen" by cron
if they are not there try adding them with this command 
```

crontab -e
LINE TO ADD TO CRONTAB

```
then try crontab -l again, if this dosent result in the line showing up try 
```
crontab
```
I dont know if that even does anything but I read something somewhere that sounded like you have to run that after adding lines.

---

