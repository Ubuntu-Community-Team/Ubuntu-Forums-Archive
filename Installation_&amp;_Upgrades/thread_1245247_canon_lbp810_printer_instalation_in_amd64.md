---
title: "canon lbp810 printer instalation in amd64"
date: 2009-08-20
forum: Installation &amp; Upgrades
---

### Post by ardhendu on 2009-08-20
unable to activate canon lbp810 in amd64 platform. pls help

---

### Post by ias on 2010-05-27
> **ardhendu said:**
> unable to activate canon lbp810 in amd64 platform. pls help

Your in luck. I've been trying to get this working on both 32 and 64 for years with no success until today. I'm now on Lucid. Here the method from the French guys who seem the specialists on this. I'm translating Rocky77's post for your
[http://forum.ubuntu-fr.org/viewtopic.php?id=207202](http://forum.ubuntu-fr.org/viewtopic.php?id=207202)

Here the method:

He describes how to compile the needed yourself, but also provided a link to download a zip with the files

[http://dl.free.fr/getfile.pl?file=/YcycEAkA](http://dl.free.fr/getfile.pl?file=/YcycEAkA)

Extract it and go to where you've put the files.
Then enter these commands in a console

```

sudo dpkg -i cndrvcups-common_1.80-1_amd64.deb
sudo dpkg -i cndrvcups-capt_1.80-1_amd64.deb

```

Then install ia32-libs through synaptic (it seems ia32-libs-gtk, which is also recommended by Rocky77 is now included in that)

Then go to /etc/init.d/ccpd and delete the contents, replacing it with this:


```

#!/bin/sh
# ccpd startup script for Canon Printer Daemon for CUPS
# Modified for Debian GNU/Linux
# by Raphael Doursenaud <rdoursenaud@free.fr>.
DAEMON=/usr/sbin/ccpd
LOCKFILE=/var/lock/subsys/ccpd
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
NAME=ccpd
DESC="Canon Printer Daemon for CUPS"
test -f $DAEMON || exit 0
case $1 in
start)
echo -n "Starting $DESC: $NAME"
start-stop-daemon --start --quiet --exec $DAEMON
echo "."
;;
stop)
echo -n "Stopping $DESC: $NAME"
start-stop-daemon --stop --quiet --oknodo --exec $DAEMON
echo "."
;;
status)
echo "$DESC: $NAME:" `pidof $NAME`
;;
restart)
echo -n "Restarting $DESC: $NAME"
start-stop-daemon --stop --quiet --oknodo --exec $DAEMON
sleep 1
start-stop-daemon --start --quiet --exec $DAEMON
echo "."
;;
*)
echo "Usage: ccpd {start|stop|status}"
exit 1
;;
esac
exit 0

```

Then install the printer

```

sudo /etc/init.d/cups restart
sudo /usr/sbin/lpadmin -p LBP-810 -m CNCUPSLBP1120CAPTK.ppd -v ccp:/var/ccpd/fifo0 -E
sudo /usr/sbin/ccpdadmin -p LBP-810 -o /dev/usb/lp0
sudo /etc/init.d/ccpd restart

```

Then go
```

sudo ccpd start

```


En esperant n'avoir rien oublié...
that is, he hopes he didn't forget anything.
And it works!

Merci Rocky77!

ias

---

