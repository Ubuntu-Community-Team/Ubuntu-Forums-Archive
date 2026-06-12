---
title: "Crontab"
date: 2008-10-07
forum: General Help
---

### Post by Barnicle on 2008-10-07
I'm trying to get a shell script (week.sh) to run automatically using crontab. Unfortunately, I think I have the command section filled out incorrectly.

```
# /etc/crontab: system-wide crontab
# Unlike any other crontab you don't have to run the `crontab'
# command to install the new version when you edit this file
# and files in /etc/cron.d. These files also have username fields,
# that none of the other crontabs do.

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# m h dom mon dow user command
17 * * * * root cd / && run-parts --report /etc/cron.hourly
25 6 * * * root test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
47 6 * * 7 root test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )
52 6 1 * * root test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )
* 11 * * * root ~/./week.sh
#
```

What I'm trying to do is run the shell script which is located inside my home directory. Hence, why I've typed '~/./week.sh', but I have a feeling that is incorrect. Can you help me please? Also, if the user is a different name than root, that needs to be specified, correct?

---

### Post by geirha on 2008-10-07
Do you intend to run it as root or as your own user?

You are right in feeling ~ is incorrect, because it is, supply the full path, like /home/yourusername/week.sh

If you want it to be run weekly, you can simply put it in /etc/cron.weekly/, but you must remove the extension, so ```
sudo mv ~/week.sh /etc/cron.weekly/week
```

---

### Post by Barnicle on 2008-10-07
Ah, finally someone responds! Thanks for that geirha.

Ok, so what I'm trying to actually do is run this script everyday at 11, and that's why I have '* 11 * * *'. Now, if I want to run this as a user named administrator, with sudo rights, what do I put exactly in the command section? I understand what you put previously, just wondering how I would do it this way.

---

### Post by GooglePlexity on 2008-10-07
* 11 * * * will run it every minute of the 11th hour - you want 0 11 * * * instead

put ./home/administrator/week.sh in the command section, so the whole line will be

```
0 11 * * * root ./home/administrator/week.sh
```

I don't believe it makes sense to run it as administrator, just run it as root

---

### Post by Barnicle on 2008-10-07
So, I don't even need to specify the user, correct?

EDIT: Just saw your revision. I will run it as root and see how it goes. Thanks guys.

---

### Post by GooglePlexity on 2008-10-07
if you're using /etc/crontab you do; if you run it as yourself than you can just use crontab -e to edit your own crontab, and you don't need to specify the user

---

### Post by geirha on 2008-10-07
> **GooglePlexity said:**
> 
0 11 * * * root ./home/administrator/week.sh


Except without that preceeding '.' there.

```
0 11 * * * root /home/administrator/week.sh
```

---

### Post by Barnicle on 2008-10-07
Alright, I'll try it out. What the script does is just moves a file to a specific folder each day. I also have a script that should run every week to do some cleaning and moving of files. That script should run every monday at 11. So, for that one I should just do this:?

```
0 11 mon * * root /home/administrator/weekly.sh
```

EDIT: I had a feeling that "." shouldn't be there. Ok, thanks.

---

### Post by geirha on 2008-10-07
Almost. The last field specifies day of week, and it won't accept names for the days, only numbers 0-7, with 0 and 7 being sunday, 1 being monday etc.

```
0 11 * * 1 root /home/administrator/weekly.sh
```

Run this to read more about how that file works:
```
man 5 crontab
```

EDIT: And I should learn to read the manual myself. It **does** accept names for the days. Sorry :)

---

### Post by Barnicle on 2008-10-07
Awesome guys. I'm a happy camper now. I already did a man on crontab, but I was still confused :) Have a great day :)

---

### Post by GooglePlexity on 2008-10-07
> **geirha said:**
> Except without that preceeding '.' there.

```
0 11 * * * root /home/administrator/week.sh
```

Hmm, I think it works either way though.

---

### Post by geirha on 2008-10-07
> **GooglePlexity said:**
> Hmm, I think it works either way though.

If cron runs the scripts from / it will work (which I think it does), but it's safest to use the absolute path :)

EDIT: And glad you got it working Barnicle, you can mark it as solved using the Thread Tools dropdown, to make it easier for others with similar problems to find a thread with a solution.

---

### Post by Barnicle on 2008-10-08
So, it seems as though it didn't work. I check today, and the file which was suppose to be moved, hadn't. I'm starting to think it's because I have the user as root, when I'm logged as administrator. I'm going to try switching the user to administrator and see what happens.

---

### Post by Barnicle on 2008-10-14
Alright, so I just check to see if the script ran, and it didn't. I'm starting to think it's because I'm running it under root, or something. Please, let me know if what I've got here is incorrect:

```
administrator@ftp:~$ sudo -s
[sudo] password for administrator:
root@ftp:~# cat /etc/crontab
# /etc/crontab: system-wide crontab
# Unlike any other crontab you don't have to run the `crontab'
# command to install the new version when you edit this file
# and files in /etc/cron.d. These files also have username fields,
# that none of the other crontabs do.

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# m h dom mon dow user  command
17 *    * * *   root    cd / && run-parts --report /etc/cron.hourly
25 6    * * *   root    test -x /usr/sbin/anacron || ( cd / && run-parts --repor                                                                            t /etc/cron.daily )
47 6    * * 7   root    test -x /usr/sbin/anacron || ( cd / && run-parts --repor                                                                            t /etc/cron.weekly )
52 6    1 * *   root    test -x /usr/sbin/anacron || ( cd / && run-parts --repor                                                                            t /etc/cron.monthly )
00 11   * * *   root    /home/administrator/week.sh
00 11   * * 1   root    /home/administrator/weekly.sh
#


root@ftp:~#

```

---

### Post by geirha on 2008-10-14
If it tries to run it, but fails, it will send you a mail about it. Install mailx if it isn't allready install, then check if root has gotten mail:
```
sudo aptitude install mailx
sudo mail
```

---

### Post by unutbu on 2008-10-14
```
00 11   * * *   root    /home/administrator/week.sh
```
Your crontab line looks fine (except that it will run daily at 11am, not weekly.)

You can check that cron tried to execute week.sh 
by looking in /var/log/syslog or /var/log/syslog.0.
There you should see something like
```
Oct 13 11:00:01 localhost /USR/SBIN/CRON[23340]: (root) CMD (**/home/administrator/week.sh**)
```

If you see this, but find week.sh did not perform as expected, then the problem is probably inside the week.sh script. In this case, please post the script.

---

### Post by Barnicle on 2008-10-14
This script is suppose to run daily. I don't care which user it runs under, as long as it runs. Basically, this script works when I run it by itself, unless there is some underlining I'm missing. I just need this script to execute on the time that is specified in the crontab:

```
administrator@ftp:~$ ls
fourweeksago  oneweekago  threeweeksago  twoweeksago  week.sh
friday        saturday    thursday       wednesday
monday        sunday      tuesday        weekly.sh
administrator@ftp:~$ cat week.sh
#! /bin/bash
declare day

day=`date '+%A'`

if [ "$day" == "Monday" ]; then
        mv ~/*.rar ~/sunday
elif [ "$day" == "Tuesday" ]; then
        mv ~/*.rar ~/monday
elif [ "$day" == "Wednesday" ]; then
        mv ~/*.rar ~/tuesday
elif [ "$day" == "Thursday" ]; then
        mv ~/*.rar ~/wednesday
elif [ "$day" == "Friday" ]; then
        mv ~/*.rar ~/thursday
elif [ "$day" == "Saturday" ]; then
        mv ~/*.rar ~/friday
elif [ "$day" == "Sunday" ]; then
        mv ~/*.rar ~/saturday
fi
administrator@ftp:~$
```

EDIT: Should I change my crontab to read '00 11   * * *   administrator    /home/administrator/week.sh' instead??

---

### Post by taladan on 2008-10-14
that's a script hurting for a case/esac statement.

```

#!/bin/bash

# Filemove script originated by Barnicle, revised by Taladan
# 10-14-2008

day=`date '+%A'`

case "$day" in
Monday) 
        mv ~/*.rar ~/sunday
        ;;
Tuesday)
        mv ~/*.rar ~/monday
        ;;
Wednesday)
        mv ~/*.rar ~/tuesday
        ;;
Thursday)
        mv ~/*.rar ~/wednesday
        ;;
Friday)
        mv ~/*.rar ~/thursday
        ;;
Saturday)
        mv ~/*.rar ~/friday
        ;;
Sunday)
        mv ~/*.rar ~/saturday

*)
        echo "Default case hit, something bad happened with date"
        exit 1
esac

```

More readable, less work and typing, and you don't have to declare variables in bash scripts.

And now I see why it's not working in your cron job.

Do a search and replace of ~/ with the full path of the script.

---

### Post by geirha on 2008-10-14
That script will copy all rar files in /root to /root/monday etc ...

Change ~ to the full path. I'm assuming it should be the administrators homedir?

Or, instead of changing ~ in the script, make the script run as the administrator user.

I'd recommend the latter.

---

### Post by Barnicle on 2008-10-14
I'm going to try just changing it to run as administrator as oppose to root first. If not, I will change the script to read /home/administrator as oppose to ~/

Thanks for the script and help guys. I will try your script if all else fails. Also, this job is suppose to run unsupervised, so I can't have the script prompting for anything. Lastly, since I have been running these scripts, do you think there are extra files taking up space elsewhere (root's directory)?

---

### Post by geirha on 2008-10-14
> **Barnicle said:**
> I'm going to try just changing it to run as administrator as oppose to root first. If not, I will change the script to read /home/administrator as oppose to ~/

Thanks for the script and help guys. I will try your script if all else fails. Also, this job is suppose to run unsupervised, so I can't have the script prompting for anything. Lastly, since I have been running these scripts, do you think there are extra files taking up space elsewhere (root's directory)?

This should give you a nice overview of disk usage in /root
```
sudo du -hx --max-depth=1 /root
```

BTW, taladan's script will not prompt for anything, though if none of the cases match, it will echo a string and exit with error. That will make cron mail you about it. (use the mail program to read such mails)

---

### Post by taladan on 2008-10-14
Here's the thing - it's not prompting for anything, and you should always put in an error case in there so that if something bad does happen, you have a log of it.  Just have your script set up to run with stderr redirected to a cron-error.log file in your home directory or make a logs directory.

Never ever let a script fail silently without giving you any feedback, it's the surest way possible to confusing yourself when it comes to figuring out why a script failed.

Tal

---

### Post by Barnicle on 2008-10-16
Changing the user name from root to administrator fixed the problem. Thanks guys for all your help.

---

