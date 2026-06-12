---
title: "Crontab Troubleshooting"
date: 2008-10-01
forum: General Help
---

### Post by connamara_john on 2008-10-01
Hello.

I am having trouble setting off a script in crontab.  First of all, I know crontab works because of this line:

*/1 * * * * /usr/bin/touch /home/jvatianou/ocmd/trunk/Build/foo

I can see that touch is working because when I do an 'ls -l', I see that the file is updated every minute.

Below is my update to crontab:

*/1 * * * * /home/jvatianou/ocmd/trunk/Build/Start

And here is the Start script itself:

#!/bin/sh
PATH=/bin:/usr/bin:/usr/local/bin:/usr/X11R6/bin:/sbin:/usr/sbin:/usr/local/sbin
export PATH

if [ -f ocmd.pid ]
then
    echo "One Chicago Market Recorder is already running!!!!"
    exit
fi

./OneChicagoMD

Pretty basic shell script, I am checking to see if the software is already running by testing for a pid file.  If the file is not found, I start my software.  I thought that maybe my problem was that I didn't have a PATH in the file, I included the PATH but still doesn't work though.

Do you see anything in particular that stands out that I'm doing wrong?  What can I do to troubleshoot this?  I tried sending output to error logs or creating some type of log, of course none of this works.  My version of Ubuntu is:

jvatianou@proto:~/ocmd/trunk/Build$ cat /etc/issue
Ubuntu 8.04.1 \n \l

Also, when I look in the /var/log/syslog, I see:

Oct  1 09:35:01 proto /USR/SBIN/CRON[14677]: (jvatianou) CMD (/home/jvatianou/ocmd/trunk/Build/Start 1> log1.log 2> errlog.log )
Oct  1 09:35:01 proto /USR/SBIN/CRON[14681]: (jvatianou) CMD (/usr/bin/touch /home/jvatianou/ocmd/trunk/Build/foo)

I don't see a cron log anywhere.  I read that a cron log exists, but cannot find it.

Any ideas would be helpful.
Thank you very much.
John

Also, just thought of something, my script is executable...
-rwxrwxrwx  1 jvatianou jvatianou     219 2008-10-01 08:56 Start

More stuff so that we can rule this out.
Cron is running...
jvatianou@proto:~/ocmd/trunk/Build$ ps -ef | grep cron
root      8094     1  0 Sep30 ?        00:00:00 /usr/sbin/cron
1001     15298 12621  0 09:51 pts/0    00:00:00 grep cron

I even added the below line to crontab to see if that works...
* * * * * date > /tmp/mydate.file

And now, I see...
jvatianou@proto:~/ocmd/trunk/Build$ cat /tmp/mydate.file
Wed Oct  1 09:53:02 CDT 2008

---

