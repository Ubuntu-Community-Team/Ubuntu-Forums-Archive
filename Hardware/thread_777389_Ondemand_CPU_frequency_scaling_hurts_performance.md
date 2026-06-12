---
title: "Ondemand CPU frequency scaling hurts performance"
date: 2008-05-01
forum: Hardware
---

### Post by Chris on 2008-05-01
The problem is that the ondemand governor should scale all CPU's at the same time instead of just the current one under load.  Because Linux constantly shifts processes around to different CPU's it makes the governor kick on and off all the time when running a single high load process.  This really hurts performance.

For example, on my Core Duo machine if I set the governor on all CPU's to 'performance' then I see nearly 100% performance boost in benchmarks (eg. 'openssl speed').  Even though the ondemand governor does work, when there is only one high load process it is constantly scaling both processors which severely negatively impacts performance.

So I end up not being able to use the ondemand scaling at all.  Anyone know of a way to get the ondemand module to kick all CPU's up to speed when any single processor gets loaded?

---

### Post by kevr on 2009-07-06
In your terminal, type:[INDENT][B]sudo gedit /etc/init.d/ondemand
[/B][/INDENT]In that file, you will notice that around Line 24 there is a snippet for setting a CPUFREQ variable to your scaling governors.

If you wish it to effect all of your processors, use "**/sys/devices/system/cpu/cpu*/cpufreq/scaling_governor**". Notice the "cpu*" has an asterisk which acts as a wild card and changes every processor scaling you have.

In my own ondemand file, I've added a further snippet to treat the percentage of load times (which was actually taken from a tutorial, not done myself). In my ondemand listed below, when load times hit 20% it increases the scale of my processors to the next level, and thus with 40% it will maximize my scales at 100%. This snippet resides on lines 30 - 34.

```
#! /bin/sh
### BEGIN INIT INFO
# Provides:          ondemand
# Required-Start:    $remote_fs $all
# Required-Stop:
# Default-Start:     2 3 4 5
# Default-Stop:
# Short-Description: Set the CPU Frequency Scaling governor to "ondemand"
### END INIT INFO


PATH=/sbin:/usr/sbin:/bin:/usr/bin

. /lib/init/vars.sh
. /lib/lsb/init-functions

case "$1" in
    start)
        start-stop-daemon --start --background --exec /etc/init.d/ondemand -- background
        ;;
    background)
    sleep 60 # probably enough time for desktop login

    for CPUFREQ in /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor
    do
        [ -f $CPUFREQ ] || continue
        echo -n performance > $CPUFREQ
    done

    for CPU_THRESHOLD in /sys/devices/system/cpu/cpu*/cpufreq/ondemand/up_threshold
    do
        [ -f $CPU_THRESHOLD ] || continue
        echo -n 20 > $CPU_THRESHOLD
    done
    ;;
    restart|reload|force-reload)
        echo "Error: argument '$1' not supported" >&2
        exit 3
        ;;
    stop)
        ;;
    *)
        echo "Usage: $0 start|stop" >&2
        exit 3
        ;;
esac
```

In fact, this worked perfectly for me. I am not extremely experienced in Linux operating systems, but I hope this post helped you. :)

If it didn't help, I apologize.

---

### Post by tsk1979 on 2010-03-25
my ondemand file did not have the echo 20 > .... block
So I added that block from a tutorial.
So after that I need to do this right?
sudo -s
/etc/init.d/ondemand stop
/etc/init.d/ondemant start

Now the problem is that normally when we start network etc., we see some output, telling us its been done, but with the above command, nothing happens on the terminal.
I am using Kubuntu.

Though I have cpu* wildcard, I see that many times only one CPU is scaled up. This is a problem watching HD videos etc.,

I run a Dell Inspiron E1505/6400 with the Intel 945 Graphics card.
After I added the THRESHOLD block, I am able to watch SD videos all right, but I still do not go to full 100% 1.6 GHz everytime. From the KDE CPU applet, I can see frequency going to 1.6GHz sometimes, but not always.
I think its working, but not as well.
Will lowering the threshold to 15 or so do the trick?

---

