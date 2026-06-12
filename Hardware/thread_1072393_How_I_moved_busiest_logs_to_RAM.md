---
title: "How I moved busiest logs to RAM"
date: 2009-02-17
forum: Hardware
---

### Post by gibson3659 on 2009-02-17
I wanted to minimize hd activity on my Ubuntu based XBMC media center, so I made the following changes.  I figured it could be applicable to laptops also.

1. Created /var/ram to store the temporary log files
2. Added this line to /etc/fstab
```
none            /var/ram        tmpfs
```
3. Moved the following in /var/ram by changing the relevant lines in /etc/syslog.conf
```
auth,authpriv.*                 /var/ram/auth.log
*.*;auth,authpriv.none         -/var/ram/syslog
daemon.*                        -/var/ram/daemon.log
kern.*                          -/var/ram/kern.log
user.*                          -/var/ram/user.log

*.=debug;\
        auth,authpriv.none;\
        news.none;mail.none     -/var/ram/debug
*.=info;*.=notice;*.=warning;\
        auth,authpriv.none;\
        cron,daemon.none;\
        mail,news.none          -/var/ram/messages

```
4. Edited /etc/cron.daily/sysklogd and /etc/cron.weekly/sysklogd to change the roll directory from . to /var/log
```
change
    savelog -g adm -m 640 -u ${USER} -c 7 $LOG >/dev/null
to
    savelog -g adm -m 640 -u ${USER} -r /var/log -c 7 $LOG >/dev/null
```
5. Applied this patch to /usr/bin/savelog
```
305,307c305,312
<                               echo "Error hardlinking $filename to $newfilename" >&2
<                               exitcode=8
<                               continue
---
>                               echo "Error hardlinking $filename to $newfilename.  Trying symlink" >&2
>                                         if ln -s -f -- "$filename" "$newfilename"; then
>                                                echo "Symlinking $filename to $newfilename succeeded.  Continuing" >&2
>                                                mv -- "$filename.new" "$filename"
>                                         else
>                                               exitcode=8
>                                               continue
>                                         fi

```
6. Clean up the relevant *., *.log and *.0 files in /var/log so they don't interfere with the symlinking.

The net effect should be that the logs are in ram and rotated to /var/log according the the normal daily or weekly schedule.  I've only been running this a day or two, so YMMV.  Does anyone see any problems with this.

---

### Post by ggarron on 2010-04-11
Hi,
The only problem I might see, is the size of the logs and the size of your RAM disk, you may want to rotate them hourly, or something and send the rotated to the original /var/log/ directory.

Regards.

Guillermo 
[http://www.go2linux.org/](http://www.go2linux.org/)

---

