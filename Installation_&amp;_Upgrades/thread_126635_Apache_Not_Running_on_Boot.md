---
title: "Apache Not Running on Boot"
date: 2006-02-07
forum: Installation &amp; Upgrades
---

### Post by WelterPelter on 2006-02-07
This is a strange little phenomenon. My apache2 is working fine, except that I have to start it manually after booting. I have it listed in System > Administration > Services as activated, and Bum has it checked as well.

Any ideas?

---

### Post by slazh on 2006-02-07
Have you tried this: [http://ubuntuforums.org/showthread.php?t=20901](http://ubuntuforums.org/showthread.php?t=20901) ?

---

### Post by WelterPelter on 2006-02-07
[QUOTE=slazh]Have you tried this: [http://ubuntuforums.org/showthread.php?t=20901](http://ubuntuforums.org/showthread.php?t=20901) ?[/QUOTE]

Yes. The trick there, which is to chmod the executable, didn't work for me.

---

### Post by WelterPelter on 2006-02-08
*bumpity bump!*:-k

---

### Post by Wide on 2006-02-08
apt-get install rcconf

Run it in from the shell & check what you want to start at boot

---

### Post by WelterPelter on 2006-02-08
Still no go. Hello from Hollywood, btw.

---

### Post by KevlarGurra on 2006-03-06
I have the same problem... There are symlinks in both /etc/rc2.d and rc5.d...still apache2 doesn't start at boot...any other suggestions?

---

### Post by WelterPelter on 2006-03-06
My problem turned out to be that both apache and apache2 were installed. I got rid of all the apache stuff, reinstalled apache2, and everything worked fine.

---

### Post by geek.de.nz on 2006-04-17
I have the same problem. but chmod +x didn't work for me. There seems to be something wrong with the apache2 script, because when I do:
```

#/etc/init.d/apache2 start

```
it doesn't start apache, but when I do
```

#/usr/sbin/apache2ctl start

```
it starts fine. The /etc/init.d/apache2 script does not give feedback like the usual init scripts. I have used Linux since quite a while and know about init scripts and the like. Could this be a problem with Kubuntu 5.10?

Here my /etc/init.d/apache2 script:
```

#!/bin/sh -e
#
# apache2               This init.d script is used to start apache2.
#                       It basically just calls apache2ctl.

ENV="env -i LANG=C PATH=/usr/local/bin:/usr/bin:/bin"

#[ `ls -1 /etc/apache2/sites-enabled/ | wc -l | sed -e 's/ *//;'` -eq 0 ] && \
#echo "You haven't enabled any sites yet, so I'm not starting apache2." && \
#echo "To add and enable a host, use addhost and enhost." && exit 0

#edit /etc/default/apache2 to change this.
NO_START=0

set -e
if [ -x /usr/sbin/apache2 ] ; then
        HAVE_APACHE2=1
else
        exit 0
fi

. /lib/lsb/init-functions

test -f /etc/default/rcS && . /etc/default/rcS
test -f /etc/default/apache2 && . /etc/default/apache2
if [ "$NO_START" != "0" -a "$1" != "stop" ]; then
        [ "$VERBOSE" != no ] && log_warning_msg "Not starting apache2 - edit /etc/default/apache2 and change NO_START to be 0.";
        exit 0;
fi

APACHE2="$ENV /usr/sbin/apache2ctl"
APACHE2CTL="$ENV /usr/sbin/apache2ctl"

apache_stop() {
        PID=""
        PIDFILE=""
        # let's try to find the pid file
        # apache2 allows more than PidFile entry in the config but only
        # the last found in the config is used
        for PFILE in `grep ^PidFile /etc/apache2/* -r | awk '{print $2}'`; do
                PIDFILE="$PFILE"
                if [ -e "$PIDFILE" ]; then
                        PID=`cat $PIDFILE`
                fi
        done

        if `apache2 -t > /dev/null 2>&1`; then
                # if the config is ok than we just stop normaly

                if [ -e "$PIDFILE" ]
                then
                        PID=`cat $PIDFILE`

                        $APACHE2 -k stop

                        CNT=0
                        while [ 1 ]
                        do
                                CNT=$(expr $CNT + 1)

                                [ ! -d /proc/$PID ] && break

                                if [ $CNT -gt 60 ]
                                then
                                        if [ "$VERBOSE" != no ]; then
                                                echo " ... failed!"
                                                echo "Apache2 failed to honor the stop command, please investigate the situation by hand."
                                        fi
                                        return 1
                                fi

                                sleep 1
                        done
                else
                        if [ "$VERBOSE" != no ]; then
                                echo -n " ... no pidfile found! not running?"
                        fi
                fi

        else
                # if we are here something is broken and we need to try
                # to exit as nice and clean as possible

                # if pidof is null for some reasons the script exits automagically
                # classified as good/unknown feature
                PIDS=`pidof apache2` || true

                REALPID=0
                # if there is a pid we need to verify that belongs to apache2
                # for real
                for i in $PIDS; do
                        if [ "$i" = "$PID" ]; then
                                # in this case the pid stored in the
                                # pidfile matches one of the pidof apache
                                # so a simple kill will make it
                                REALPID=1
                        fi
                done

                if [ $REALPID = 1 ]; then
                        # in this case it is everything nice and dandy
                        # and we kill apache2
                        kill $PID
                else
                        # this is the worst situation... just kill all of them
                        #for i in $PIDS; do
                        #       kill $i
                        #done
                        # Except, we can't do that, because it's very, very bad
                        if [ "$VERBOSE" != no ]; then
                                echo " ... failed!"
                                echo "You may still have some apache2 processes running.  There are"
                                echo "processes named 'apache2' which do not match your pid file,"
                                echo "and in the name of safety, we've left them alone.  Please review"
                                echo "the situation by hand."
                        fi
                        return 1
                fi
        fi
}

# Stupid hack to keep lintian happy. (Warrk! Stupidhack!).
case $1 in
        start)
                [ -f /etc/apache2/httpd.conf ] || touch /etc/apache2/httpd.conf
                #ssl_scache shouldn't be here if we're just starting up.
                [ -f /var/run/apache2/ssl_scache ] && rm -f /var/run/apache2/*ssl_scache*
                log_begin_msg "Starting web server (Apache2)..."
                if $APACHE2CTL startssl; then
                        log_end_msg 0
                else
                        log_end_msg 1
                fi
        ;;
        stop)
                log_begin_msg "Stopping web server (Apache2)..."
                if apache_stop; then
                        log_end_msg 0
                else
                        log_end_msg 1
                fi
        ;;
        reload)
                log_begin_msg "Reloading web server config..."
                if $APACHE2CTL graceful $2 ; then
                        log_end_msg 0
                else
                        log_end_msg 1
                fi
        ;;
        restart | force-reload)
                log_begin_msg "Forcing reload of web server  (Apache2)..."
                if ! apache_stop; then
                        log_end_msg 1
                fi
                if $APACHE2CTL startssl; then
                        log_end_msg 0
                else
                        log_end_msg 1
                fi
        ;;
        *)
                log_success_msg "Usage: /etc/init.d/apache2 start|stop|restart|reload|force-reload"
        ;;
esac

```

I don't really need apache running at boot time, but it would help some other people probably, because quite a few people seem to have this problem.

---

### Post by geek.de.nz on 2006-05-10
After reading through the script a little bit, I found the following:
```

#edit /etc/default/apache2 to change this.
NO_START=0

```

So, I just edited /etc/default/apache2 and changed the value there to:
```

NO_START=0

```
because the script checks what this value is and accordingly lets apache start or not:
```

test -f /etc/default/apache2 && . /etc/default/apache2
if [ "$NO_START" != "0" -a "$1" != "stop" ]; then
        [ "$VERBOSE" != no ] && log_warning_msg "Not starting apache2 - edit /etc/default/apache2 and change NO_START to be 0.";
        exit 0;
fi

```

Hope that helps some with a confusion here.

---

