---
title: "Need to add a script to system startup"
date: 2008-09-09
forum: General Help
---

### Post by akudewan on 2008-09-09
Hi,

I need to add a script to my system startup (not Gnome startup). This is what I've made:
```

#!/bin/bash
# /etc/init.d/keeponline-launch
DAEMON=/usr/local/bin/keeponline.sh

test -x $DAEMON || exit 0

case "$1" in
	start)
		echo "Starting keeponline..."
		start-stop-daemon --start --exec $DAEMON
	;;

	stop)
		echo "Stopping keeponline"
		start-stop-daemon --stop --exec $DAEMON
	;;

	*)
		echo "Usage: /etc/init.d/keeponline-launch {start|stop}"
		exit 1
		;;
esac

exit 0

```

Some issues:
1) I need to start this only after the network interface is up. How can I make sure of this?
2) The actual script (keeponline.sh), is not a daemon, just a bash script. Will it work with start-stop-daemon ?
3) The keeponline.sh script runs in an infinite loop, waking up every 10 minutes, will this cause any problems in the startup?

Thanks :)

---

### Post by u-slayer on 2008-09-10
add your script to /etc/rc.local):P

---

### Post by kerry_s on 2008-09-10
i would put it in a cron job instead. install gnome-schedule if you want a gui.

---

### Post by akudewan on 2008-09-10
> **kerry_s said:**
> i would put it in a cron job instead. install gnome-schedule if you want a gui.

I had actually used a cron job earlier. But there was the matter of [excessive logging to syslog]("http://www.linuxquestions.org/questions/linux-general-1/disable-cron-from-logging-to-syslog-653876/"). So I wanted to try this method instead.

@u-slayer: I'll try to use /etc/rc.local. It doesn't need a start/stop script like init.d, does it ?

---

### Post by kerry_s on 2008-09-10
> I had actually used a cron job earlier. But there was the matter of excessive logging to syslog. So I wanted to try this method instead.

you know system log is configurable right? /etc/syslog.conf
i turn most of mine off to reduce hd use.

---

### Post by Vivaldi Gloria on 2008-09-10
> **akudewan said:**
> I need to start this only after the network interface is up. How can I make sure of this?

Create a root owned file "/etc/network/if-up.d/yourscript" containing the script and make it executable. The files in this folder are run when a network connection is established.

---

### Post by akudewan on 2008-09-12
> **Vivaldi Gloria said:**
> Create a root owned file "/etc/network/if-up.d/yourscript" containing the script and make it executable. The files in this folder are run when a network connection is established.

Awesome! just what I needed :)

The final script looks like this
akudewan@ranjandesk:~$ cat /etc/network/if-up.d/keeponline-launch
```

#!/bin/bash

# Not for loopback!
[ "$IFACE" != "lo" ] || exit 0

sh /usr/local/bin/keeponline.sh &

exit 0

```

---

