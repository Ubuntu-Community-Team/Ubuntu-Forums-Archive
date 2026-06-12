---
title: "No Sound, and I broke it.  :-("
date: 2005-09-20
forum: Hardware &amp; Laptops
---

### Post by CRXSi90 on 2005-09-20
Hi, I've had Ubuntu Warty installed for about 6 months.  When Ubuntu originally installed, sound worked.  Eariler this summer, I think I was trying to get MP3s to play when I messed up my sound.  Now Ubuntu doesn't make a peep (not even at the startup screen prompting for username).  I can't remember what I did to mess it up, and I didn't know how to fix it, so I just left it.  

Now I have regained my desire to play music.  Reading some other posts, I found something that might be part of the problem.  When I type "/etc/init.d/alsa restart" in the console, it gives this error: "/etc/init.d/alsa: line 8: log_failure_msg: command not found"

Here is what the file "/etc/init.d/alsa" contains:
```
#!/bin/sh

set -e

PATH=/usr/local/sbin:/sbin:/usr/sbin:/usr/local/bin:/bin:/usr/bin

if [ "$(id -u)" != "0" -a "$1" != "--help" -a "$1" != "help" -a ! -z "$1" ]; then
    log_failure_msg "$0: To $1 ALSA, you must be root."
    exit 1
fi

# Default settings
alsactl_store_on_shutdown="autosave always"
runlevels_save='[2-5]'

[ -e /etc/default/alsa ] && . /etc/default/alsa
test -f /lib/lsb/init-functions || exit 1
. /lib/lsb/init-functions

case "$1" in
    start)
        # unmute
	for control in "PCM" "Synth" "Master" "CD" "Headphone"; do
		amixer -q set "$control" "70%" unmute 2>/dev/null || true
	done

	log_begin_msg "Restoring ALSA mixer settings..."
	if alsactl restore > /dev/null 2>&1; then
	    log_end_msg 0
	else
	    alsactl restore
	    log_end_msg 1
	    exit 1
	fi
	;;
    stop)
	if [ "$alsactl_store_on_shutdown" != "never autosave" ]; then
	    if runlevel | grep -E "^$runlevels_save " > /dev/null 2>&1 \
	    || runlevel | grep -E " $runlevels_save\$" > /dev/null 2>&1; then
		log_begin_msg "Storing ALSA mixer settings..."
		alsactl store > /dev/null 2>&1
	        log_end_msg $?
	    fi
	fi
	;;
    restart|reload)
	$0 stop && $0 start
	;;
    *)
	log_success_msg "Usage: /etc/init.d/alsa {start|stop|restart|reload}"
	exit 1
	;;
esac
```

and here is what "lspci" lists for my soundcard:
0000:00:0b.0 Multimedia audio controller: Yamaha Corporation YMF-724F [DS-1 Audio Controller] (rev 03)

Thanks in advance for the help getting my sound back!  

Kevin

---

