---
title: "weird hellanzb problem"
date: 2008-11-23
forum: General Help
---

### Post by netlemon on 2008-11-23
Since I upgraded from 7.10 to 8.10 I have a problem with starting Hellanzb with the daemon I downloaded somewhere. The daemon makes Hella start in a screen which I can recall thru "screen -x". But since I upgraded Ubuntu that doesnt work anymore. I still use "sudo /etc/init.d/hellanzb start" and I get the message that Hella started succesfully. When I try to stop it thru the daemon it says there's no such PID active. When I try "sudo killall hellanzb" it says there's no such process active.

But when I start Hellanzb using "sudo screen /bin/usr/hellanzb" it starts up fine. When i go ^A-d it detaches the screen, but I can't recall it with either "Screen -x" or "screen -r". BUT! When i look it up in my Top it runs fine. And when I place an NZB file in the daemon.queue and start up my bandwidth monitor it downloads perfectly. And after the downloaden the finished downloads is located at the right directory.

Is this a weird problem or what? Below you can find my daemon file for hellanzb.

EDIT: I already tried uninstalling (using --purge) and reinstalling screen and hellanzb.

```
#! /bin/bash
#
### BEGIN INIT INFO
# Provides:		hellanzb, hellahella
# Required-Start:	$network $local_fs
# Required-Stop:
# Default-Start:	2 3 4 5
# Default-Stop:		0 1 6
# Short-Description:	Usenet Binary Downloader
### END INIT INFO
#
# hellanzb       Start the hellanzb and hellahella
#
# hellanzb init-script v0.6 dedicated
# 
# the following vars are used:
# NAME= leave it to hellanzb, its just a display name and it is used to connect to it with screen
# USERNAME= your username, this is used to run hellanzb in
# *_PIDFILE= the pid file which the script checks
# WEBIF_ENABLED if you are running hellahella and want this to start with hellanzb
#



NAME=hellanzb
NAMEWEB=hellahella
USERNAME=chris
HELLANZB_PIDFILE=/var/run/hellanzb.pid
HELLAHELLA_PIDFILE=/var/run/hellahella.pid
WEBIF_ENABLED=0
HELLANZB_BIN=/usr/bin/hellanzb
HELLAHELLA_INI=/opt/hellahella/hella.ini
DESC="Binary Usenet Download Services:"

trap "" 1
export LANG=C

. /lib/lsb/init-functions

case "$1" in
  start)
    log_action_msg "Starting $DESC"

    log_daemon_msg "   Starting $NAME.."
    if start-stop-daemon -S -c $USERNAME -m -b --pidfile $HELLANZB_PIDFILE --exec /usr/bin/screen -- -S $NAME -D -m $HELLANZB_BIN; then
	    log_end_msg 0
	else
	    log_end_msg 1
	fi
	if test "$WEBIF_ENABLED" != "0"; then
            log_daemon_msg "   Starting $NAMEWEB.."
	    if start-stop-daemon -S -c $USERNAME -m -b --pidfile $HELLAHELLA_PIDFILE --exec /usr/bin/screen -- -S $NAMEWEB -D -m paster serve $HELLAHELLA_INI; then
	    	log_end_msg 0
	    else
		log_end_msg 1
	    fi
	fi
    ;;

  stop)
    log_action_msg "Stopping $DESC"
    log_daemon_msg "   Stopping $NAME.."
        if start-stop-daemon -K --pidfile $HELLANZB_PIDFILE; then
	    log_end_msg 0
	else
	    log_end_msg 1
	fi
	if test "$WEBIF_ENABLED" != "0"; then
    	    log_daemon_msg "   Stopping $NAMEWEB.."
	    if start-stop-daemon -K --pidfile $HELLAHELLA_PIDFILE; then
	    	log_end_msg 0
	    else
		log_end_msg 1
	    fi
	fi
    ;;

  restart)
    $0 stop
    $0 start
    ;;
  *)
    echo "Usage: /etc/init.d/$NAME start|stop|restart}"
    exit 1
    ;;
esac

exit 0

```

---

### Post by netlemon on 2008-11-25
I hope no one blames me for *bump*ing?

---

### Post by netlemon on 2009-01-18
Bump2

---

### Post by stderr on 2009-01-18
Hi netlemon

I normally use nzb and grabit myself, and don't tend to make much use of the screen command. Hellanzb looks quite neat though - may try it out later. 

If you're starting screen as root, maybe you also need to run screen -x or -r with sudo? 

As for the daemon you've downloaded, is this just the hella init.d script? It would appear as though it's the initialisation script and another package too - 'hellahella' or something? What is this & where did you get it from? It's not in the repos. 

Just done a search - is this what we're discussing? [http://www.hellanzb.com/trac/wiki/HellaHella]("http://www.hellanzb.com/trac/wiki/HellaHella"). Once we know what we're talking about, maybe we can help fix it :)

---

### Post by sosolala on 2009-01-28
Hi,

Had a look at your start script and made a few changes I like share with you. 

Please have a look and let me know if this what you wanted :-) 
Let me know, cheers,

Ruben

> 

#! /bin/bash
#
### BEGIN INIT INFO
# Provides:		hellanzb, hellahella
# Required-Start:	$network $local_fs
# Required-Stop:
# Default-Start:	2 3 4 5
# Default-Stop:		0 1 6
# Short-Description:	Usenet Binary Downloader
### END INIT INFO
#
# hellanzb       Start the hellanzb and hellahella
#
# hellanzb init-script v0.6 dedicated
# 
# the following vars are used:
# NAME= leave it to hellanzb, its just a display name and it is used to connect to it with screen
# USERNAME= your username, this is used to run hellanzb in
# *_PIDFILE= the pid file which the script checks
# WEBIF_ENABLED if you are running hellahella and want this to start with hellanzb
#



NAME=hellanzb
USERNAME=ruben
HELLANZB_PIDFILE=/var/run/hellanzb.pid
HELLANZB_BIN=/usr/bin/hellanzb
DESC="Binary Usenet Download Services:"

trap "" 1
export LANG=C

. /lib/lsb/init-functions

case "$1" in
  start)
    log_action_msg "Starting $DESC"

    log_daemon_msg "   Starting $NAME.."
    if start-stop-daemon -S -c $USERNAME -b --exec $HELLANZB_BIN  -- -D ; then
	    log_end_msg 0
	else
	    log_end_msg 1
	fi

    ;;

  stop)
    log_action_msg "Stopping $DESC"
    log_daemon_msg "   Stopping $NAME.."
        if start-stop-daemon -K --name $NAME ; then
	    log_end_msg 0
	else
	    log_end_msg 1
	fi
    ;;

  status)
  	ps  -C $NAME && $HELLANZB_BIN status
    ;;


#  restart)
#    $0 stop
#    sleep 2
#    $0 start
#    ;;
  *)
    echo "Usage: /etc/init.d/$NAME start|stop|status}"
    exit 1
    ;;
esac

exit 0




---

### Post by fnandocc on 2009-01-30
I just added "hellanzb" to the autostart session manager.

Using zussaweb as for frontend/status.

P.S. Might wanna try the "hellanzb -D" to run as a daemon.

---

