---
title: "Canon LBP 2900 n Jaunty"
date: 2009-04-29
forum: Hardware
---

### Post by ravenax on 2009-04-29
hi... the driver given in canon site(1.60/1.80) doesn't seem to work on jaunty... says "Error: Depedency is not satisfied" :confused:

what to dooo??? ](*,)

---

### Post by Jazzzyman on 2009-05-03
Have the same problem my 2900 dont work on ubuntu 9.04

---

### Post by ravenax on 2009-05-11
i got the driver to install properly...

just did 

```
sudo apt-get install -f
```

and then installed the two .deb packages that comes with the 1.60 driver version! 

everything worked out just fine! :)

---

### Post by vorros on 2009-05-13
hi!

i'm new to ubuntu ):P

i also can't seem to make my lbp2900 work.
i have tried 1.60 and 1.80 as mentioned.
they both install (both files in both versions).
printer is recognised when i plug it in.
it says "ready" in status line, but when i try printing (test page or anything else) it says "idle -printer busy" in status line.
tray icon says "lbp2900 may not be connected"

any ideas?

:(

---

### Post by nubbe on 2009-05-19
I got the same result with canon lbp 1120.

---

### Post by alex.rainy on 2009-05-21
Hi!
The same problem. I've installed 1.60 driver package from Canon website, but still can't see my model in the driver list when trying to install it (printer).

---

### Post by karl3 on 2009-05-27
try installing 1.30 derivers. worked for me.
[http://www.sendspace.com/file/defqlm](http://www.sendspace.com/file/defqlm)

follow this tutorial:
[https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/Canon_LBP_2900](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/Canon_LBP_2900)

and just use the script below instead of the suggested in step 5:
```
#!/bin/sh
# startup script for Canon Printer Daemon for CUPS (ccpd)

if [ -f /etc/rc.d/init.d/functions ]; then
	if [ -f /etc/slackware-version ]; then
		SYS_F="SL"
	else
		. /etc/rc.d/init.d/functions 
		SYS_F="RH"
	fi
elif [ -x /sbin/startproc ]; then
	SYS_F="Su"
elif [ -x /sbin/start-stop-daemon ]; then
	SYS_F="De"
fi

DAEMON=/usr/sbin/ccpd
LOCKFILE=/var/lock/subsys/ccpd

export PATH=$PATH:/usr/local/sbin:/usr/local/bin

ccpd_start ()
{
	echo -n "Starting ${DAEMON}: "
	
	if [ "$SYS_F" = "RH" ]; then	
		daemon ${DAEMON}
		[ "$?" = "0" ] && touch ${LOCKFILE}
		echo "."
	elif [ "$SYS_F" = "Su" ]; then
		startproc ${DAEMON}
		echo "."
	elif [ "$SYS_F" = "De" ]; then
		start-stop-daemon --start --quiet --oknodo --exec ${DAEMON}
		echo "."
	else
		`${DAEMON}`
	fi
}

ccpd_stop ()
{
	echo -n "Shutting down ${DAEMON}: "
	
	if [ "$SYS_F" = "De" ]; then
		start-stop-daemon --stop --quiet --oknodo --signal 15 --exec ${DAEMON}
		echo "."
	elif [ "$SYS_F" = "SL" ]; then
		kill -KILL `pidof ${DAEMON}`
		[ "$?" = "0" ] && rm -f ${LOCKFILE}
		echo 
	else
		killproc ${DAEMON}
		[ "$?" = "0" ] && rm -f ${LOCKFILE}
		echo	
	fi
}


case $1 in

	start)
		ccpd_start
		;;
		
	stop)
		ccpd_stop
		;;
	
	status)
		echo "${DAEMON}:" `pidof ${DAEMON}`
		;;
	
	restart)
		ccpd_stop
		ccpd_start
		;;
	
	*)
		echo "Usage: ccpd {start|stop|status}"
		exit 1
		;;
esac
exit 0
```
this one came with 1.80 drivers x)

---

### Post by ravenax on 2009-08-23
yayyyyyyyy THIS WORKS PERFECTLY FINE FOR ME :guitar::guitar:

---

### Post by ArsNatura on 2009-08-28
> **ravenax said:**
> yayyyyyyyy THIS WORKS PERFECTLY FINE FOR ME :guitar::guitar:

Wich driver version has worked for you? 1.30, 1.60 or 1.80?

---

### Post by netlaptop on 2010-03-17
How's about the 64 bits version of Ubuntu 9.10?
 [QUOTE=karl3;7353674]try installing 1.30 derivers. worked for me.
[http://www.sendspace.com/file/defqlm](http://www.sendspace.com/file/defqlm)
... step 5:
[code]#!/bin/sh
# startup script for Canon Printer Daemon for CUPS (ccpd)

if [ -f /etc/rc.d/init.d/functions ]; then
	if [ -f /etc/slackware-version ]; then
		SYS_F="SL"
	else
		. /etc/rc.d/init.d/functions 
		SYS_F="RH"
	fi
elif [ -x /sbin/startproc ]; then
	SYS_F="Su"
elif [ -x /sbin/start-stop-daemon ]; then
	SYS_F="De"
fi

DAEMON=/usr/sbin/ccpd
LOCKFILE=/var/lock/subsys/ccpd

export PATH=$PATH:/usr/local/sbin:/usr/local/bin

ccpd_start ()
{
	echo -n "Starting ${DAEMON}: "
	
	if [ "$SYS_F" = "RH" ]; then	
		daemon ${DAEMON}
		[ "$?" = "0" ] && touch ${LOCKFILE}
		echo "."
	elif [ "$SYS_F" = "Su" ]; then
		startproc ${DAEMON}
		echo "."
	elif [ "$SYS_F" = "De" ]

---

