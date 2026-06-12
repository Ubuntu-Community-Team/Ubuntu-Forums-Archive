---
title: "Waiting for USB disk spin up"
date: 2007-01-10
forum: Hardware &amp; Laptops
---

### Post by papalagi on 2007-01-10
I have this script in my /etc/init.d/  that starts aMule on boot:


 >  PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
 DAEMON=/usr/bin/amuled
# WEB=/usr/bin/amuleweb
 WEB=none
 NAME=amuled
 DESC=amuled
 RUNAMULE=yes
 USER=mulo

 
 test -x $DAEMON || exit 0

 
 # Include amule defaults if available
 if [ -f /etc/default/amuled ] ; then
     . /etc/default/amuled
 fi

 if [ "$RUNAMULE" != "yes" ];then
     echo "Amule not to be started. Edit /etc/default/amuled first."
     exit 1
 fi

 
 set -e

 
 case "$1" in
   start)
     echo -n "Starting $DESC: "
        su $USER -c "$DAEMON -f"
        sleep 20
        su $USER -c "$WEB --quiet &"
     echo "$NAME."
     ;;
   stop)
     echo -n "Stopping $DESC: "
        killall --quiet --ignore-case $WEB
        killall --quiet --ignore-case $DAEMON
     echo "$NAME."
     ;;
   restart|force-reload)
     echo -n "Restarting $DESC: "
        killall --quiet --ignore-case $WEB
        killall --quiet --ignore-case $DAEMON
     sleep 1
        su $USER -c "$DAEMON -f"
        sleep 20
        su $USER -c "$WEB --quiet &"
     echo "$NAME."
     ;;
   *)
     N=/etc/init.d/$NAME
     echo "Usage: $N {start|stop|restart|force-reload}" >&2
     exit 1
     ;;
 esac

 
 exit 0

 the problem is that the directory aMule searches for at startup are on an external USB disk, and at avery boot i find out aMuled switched to default directories ignoring the one specified in its config file

 i think aMule can't find the directory at startup because the USB disk takes too long to be recognised

 is there a way to delay aMule launch or make it wait for the USB disk to be recognised?
 

 any hint greatly appreciated

---

### Post by kidders on 2007-01-10
Hi there,

Would something like this be too hacky?

```
if [ -z "`mount | grep "^/dev/sdc1"`" ]; then
	echo -n "Waiting for external filesystem"
	while [ -z "`mount | grep "^/dev/sdc1"`" ]; do
		sleep 1
		echo -n "."
	done
	echo "."
fi
```

I suppose only having it wait a finite amount of time would be a worthwhile tweak!

---

### Post by papalagi on 2007-01-10
allright, your method seems to work perfectly, thank you!

---

### Post by kidders on 2007-01-10
No problem. :-) You *really* should think about tweaking my "while" loop though, especially since scripts in /etc/init.d can be run during boot ... a maximum wait of, say, 10 seconds might be in order before aborting the service startup, so you won't ever end up with an infinite loop.

---

### Post by papalagi on 2007-01-10
i appreciate your advices, but have no knowledge of this kind of scripting, i hope that anyway all the scripts are run "in parallel", not one after the other, so that anyway the system can continue booting

---

### Post by kidders on 2007-01-10
Ohh... not necessarily. Some distros support parallel execution of startup scripts. I'm not sure whether Ubuntu is one of them. In any case, it's something that can have very odd side-effects and is _not_ to be recommended. Most of the trouble with parallel boot-time script execution stems from trying to figure out the order in which scripts should be executed, and what should happen if one of them fails unexpectedly.

If you're going to play with the contents of /etc/init.d you really, ***really*** need to be reasonably confident with shell scripting. Even tiny errors can have devastating consequences. Since they tend to run as root, you should _never_ make modifications suggested on a forum/website that you don't fully understand.

Anyhow, here is a less dangerous version. It will stop waiting for a missing filesystem after 5 seconds.

```
DEV=/dev/sdc7

function check_fs {
	if [ -z "`mount | grep "^$DEV"`" ]; then
		echo -n "Waiting for $DEV to mount"
		for i in `seq 1 5`; do
			sleep 1
			echo -n "."
			if [ -n "`mount | grep "^$DEV"`" ]; then
				return 1
			fi
		done
		return 0
	else
		echo -n "$DEV is ready"
		return 1
	fi
}

check_fs
if [ $? -eq 1 ]; then
	echo " [OK]"
	# Place code here
else
	echo " [FAILED]"
	# The filesystem didn't appear :-(
fi
```

---

