---
title: "Starting and Stopping VSFtpd with Cron"
date: 2005-11-22
forum: General Help
---

### Post by Roman27 on 2005-11-22
I work during the day and would like to have the ability to transfer files to and from work.  I setup VSFtp for that purpose.  But I don't want VSFtp to run all the time.  I'm only at work Monday - Friday from 7:00am to 4:00pm.  So, I decided to create a cron job to handle it.

```
sudo crontab -l
0 7 * * 1-5 /etc/init.d/vsftpd start >/dev/null 2>&1
0 16 * * 1-5 /etc/init.d/vsftpd stop >/dev/null 2>&1
```

Unfortunately, it doesn't work.  Anyone know why?  :confused: 

Also, if I didn't put the *>/dev/null* at the end would cron e-mail me results?  Where do I go to check that mail?

---

### Post by Burke on 2005-11-22
I think it may have to do with the spaces.  Try: 

0 7 * * 1-5 "/etc/init.d/vsftpd start" >/dev/null 2>&1
0 16 * * 1-5 "/etc/init.d/vsftpd stop" >/dev/null 2>&1

---

### Post by Roman27 on 2005-11-22
Good idea, but no change.  :(

---

### Post by Roman27 on 2005-11-23
Anybody have an idea on this?  I would think someone has run into this before besides me.

---

### Post by Roman27 on 2005-11-30
Ok, I have some further info on this issue.  I tried:```
23 8 * * * /etc/init.d/vsftpd start  >& debug.log
```
...which works fine when running it from the command line.  :confused:

Anyway, the debug.log file looks like:```
 * Starting FTP server: vsftpd
/etc/init.d/vsftpd: line 23: start-stop-daemon: command not found
   ...fail!
```
The vsftpd script looks like:```
#!/bin/sh
# /etc/init.d/vsftpd
#
# Written by Sander Smeenk <ssmeenk@debian.org>

set -e

# Exit if vsftpd.conf doesn't have listen=yes or listen_ipv6=yes
# (mandatory for standalone operation)
if [ -f /etc/vsftpd.conf ] && ! egrep -iq "^ *listen(_ipv6)? *= *yes" /etc/vsftpd.conf; then 
    exit 0
fi

DAEMON=/usr/sbin/vsftpd
NAME=vsftpd

test -x $DAEMON || exit 0
. /lib/lsb/init-functions

case "$1" in
  start)
    log_begin_msg "Starting FTP server: $NAME"
    start-stop-daemon --start --background -m --pidfile /var/run/vsftpd/vsftpd.pid --exec $DAEMON && log_end_msg 0 || log_end_msg 1
    ;;
  stop)
    log_begin_msg "Stopping FTP server: $NAME"
    start-stop-daemon --stop --pidfile /var/run/vsftpd/vsftpd.pid --oknodo --exec $DAEMON && log_end_msg 0 || log_end_msg 1
    ;;
  restart)
    $0 stop
    $0 start
    ;;
  reload|force-reload)
    log_begin_msg "Reloading $NAME configuration files"
    start-stop-daemon --stop --pidfile /var/run/vsftpd/vsftpd.pid --signal 1 --exec $DAEMON && log_end_msg 0 || log_end_msg 1
    ;;
  *)
    log_success_msg "Usage: /etc/init.d/$NAME {start|stop|restart|reload}"
    exit 1
    ;;
esac

exit 0
```
Why is it not able to work via cron when it works so nice on the command line?

---

### Post by Roman27 on 2005-11-30
Ok, I figured it out on my own.

I assumed that the root crontab ran as root and had the same environment as root.  I was wrong.  :( 

Here was my thought process...

From my previous post, you can see the error```
/etc/init.d/vsftpd: line 23: start-stop-daemon: command not found
```
Uhhh...  Ok, so where is *start-stop-daemon*?  Let's find out:

```
dim8300:~$ whereis start-stop-daemon
start-stop-daemon: /sbin/start-stop-daemon
```
Hmmm...  It's in /sbin.  But why can't cron get there?  It's running as root, and root can get there without a problem.  Let's see here...  Maybe cron doesn't use the same path?

```
dim8300:~# crontab -e
0 15 * * * echo $PATH >& debug.log
``````
dim8300:~# cat debug.log
/usr/bin:/bin
```
What the heck?!?  That path is tiny!  Where is /sbin?  How do I add that in?

> _From crontab(5)_
Several environment variables are set up automatically by  the  cron daemon.  SHELL is set to /bin/sh, and LOGNAME and HOME are set from the /etc/passwd  line  of   the   crontab's   owner.   PATH   is   set   to "/usr/bin:/bin".   HOME,  SHELL, and PATH may be overridden by settings in the crontab; LOGNAME is the user that the job is running  from,  and may not be changed.
Grrr....  Stupid cron!  ](*,) 

```
dim8300:~# crontab -e
PATH=/usr/bin:/bin:/sbin
```
DING!  Now it works.  That's the end of that.  ...hopefully.  ;)

---

