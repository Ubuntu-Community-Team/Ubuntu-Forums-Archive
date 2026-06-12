---
title: "acpid, powernowd, and 'nice'"
date: 2005-11-03
forum: Hardware &amp; Laptops
---

### Post by saik0 on 2005-11-03
I run Folding @ Home on all my PCs, but on my laptop I want powernowd to scale frequency for it, and all 'nice'd apps, when it's plugged in but to ignore them when it's running on battery power. As far as I can tell i would have to edit /etc/init.d/powernowd to check the acpi status on bootup, and /etc/acpi/power.sh which is run by /etc/acpi/events/ac when It's plugged in/unplugged. Problem is i dont understand half of the stuff going on in the scripts. Any help?

/etc/init.d/powernowd
```
#! /bin/sh

PATH=/sbin:/bin:/usr/sbin:/usr/bin
DAEMON=/usr/sbin/powernowd
NAME=powernowd
DESC=powernowd

test -x $DAEMON || exit 0

# create the file /etc/default/powernowd if you want to override the value of
# variable OPTIONS and change the default behavior of the daemon as launched

OPTIONS="-q"
[ -f /etc/default/$NAME ] && . /etc/default/$NAME

# Get lsb functions
. /lib/lsb/init-functions
. /etc/default/rcS

if [ "x$VERBOSE" = "xno" ]; then
        MODPROBE_OPTIONS="$MODPROBE_OPTIONS -Q"
        export MODPROBE_OPTIONS
fi

set -e

load_modules() {
        #stop the kernel printk'ing at all while we load.
        PRINTK=`cat /proc/sys/kernel/printk`
        [ "$VERBOSE" = no ] && echo "0 0 0 0" > /proc/sys/kernel/printk

        #build a list of current modules so we don't load a module twice
        LIST=`/sbin/lsmod|awk '!/Module/ {print $1}'`

        #get list of available modules
        LOC="/lib/modules/`uname -r`/kernel/drivers/cpufreq"
        if [ -d $LOC ]; then
          MODAVAIL=`( find $LOC -type f -name "*.o" -printf "basename %f .o\n"; \
                   find $LOC -type f -name "*.ko" -printf "basename %f .ko\n" ) | /bin/sh`
        else
          MODAVAIL=""
        fi


        #echo "Loading cpufreq modules:"
        for mod in $MODAVAIL; do
        #        echo "     $mod"
                echo $LIST| grep -q -w "$mod" || modprobe $mod >/dev/null || /bin/true
        done

        #cpufreq is built in on powerpc; just return
        if [ "`uname -m`" = "ppc" ]; then
                return 0
        fi


        #new style detection system
        if [ ! "$FREQDRIVER" = "" ]; then
                modprobe "$FREQDRIVER"
        else
                . /usr/share/powernowd/cpufreq-detect.sh
                [ ! -z "$MODULE" ] && (modprobe "$MODULE"||modprobe "$MODULE_FALLBACK")
        fi

        if [ "$USE_OLD_DETECT" = "fish" ]; then
        # now lets load the driver
        if [ ! $FREQDRIVER = "" ]; then
                modprobe $FREQDRIVER||true
        fi
        if [ "`uname -m`" = "x86_64" ]; then
                modprobe powernow-k8 >/dev/null 2>&1||true
        fi

        if [ ! -f /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor ]; then
                modprobe acpi > /dev/null 2>&1|| true
        fi
        fi
        echo "$PRINTK" > /proc/sys/kernel/printk
}

check_kernel() {
        CPUFREQ=/sys/devices/system/cpu/cpu0/cpufreq

        if [ -f "$CPUFREQ/scaling_governor" ] && \
                [ -f "$CPUFREQ/scaling_available_governors" ] && \
                grep -q userspace "$CPUFREQ/scaling_available_governors"
        then
                return 0
        else
                return 1
        fi
}

start() {
        log_begin_msg "Starting $DESC... "
        if check_kernel
        then
        #       echo "Starting $DESC: "
                start-stop-daemon --start --quiet --oknodo --exec $DAEMON -- $OPTIONS >/dev/null 2>&1 || {
                    status=$?
                    log_end_msg $status
                    return $status
                }
        else
                log_success_msg "CPU frequency scaling not supported"
        #       echo "required sysfs objects not found!"
        #       echo -e "\tRead /usr/share/doc/powernowd/README.Debian for more information."
        fi
        log_end_msg 0
        return 0
}

case "$1" in
  start)
        [ -f /proc/modules ] && load_modules
        start
        ;;
  stop)
        log_begin_msg "Stopping $DESC: "
        start-stop-daemon --stop --quiet --oknodo --exec $DAEMON
        log_end_msg $?
        ;;
  restart|force-reload)
        $0 stop
        sleep 1
        $0 start
        #echo "$NAME."
        ;;
  *)
        N=/etc/init.d/$NAME
        log_success_msg "Usage: $N {start|stop|restart|force-reload}" >&2
        exit 1
        ;;
esac

exit 0

```

/etc/acpi/power.sh
```
#!/bin/sh

. /etc/default/acpi-support
. /usr/share/acpi-support/power-funcs

getState;

checkStateChanged;

grep -q off-line /proc/acpi/ac_adapter/*/state
if [ $? = 0 ] && [ x$1 != xstop ]; then

    if [ x$ENABLE_LAPTOP_MODE = xtrue ]; then
        $LAPTOP_MODE start

        if [ -d /sys/bus/ide ]; then
            for x in /sys/bus/ide/devices/*/block; do
                drive=$(basename $(readlink $x));
                $HDPARM -S 12 /dev/$drive
                #$HDPARM -B 1 /dev/$drive
            done
        fi

#       if [ -d /sys/bus/scsi ]; then
#           for x in /sys/bus/scsi/devices/*/block; do
#               drive=$(basename $(readlink $x));
#               $HDPARM -S 12 /dev/$drive
#               #$HDPARM -B 1 /dev/$drive
#           done
#       fi
    fi

    for x in /tmp/.X11-unix/*; do
        displaynum=`echo $x | sed s#/tmp/.X11-unix/X##`
        getXuser;
        if [ x"$XAUTHORITY" != x"" ]; then
            export DISPLAY=":$displaynum"
            su $user -c "xscreensaver-command -throttle" &
            xset dpms 0 0 120
        fi
    done
else
    if [ x$ENABLE_LAPTOP_MODE = xtrue ]; then
        if [ -d /sys/bus/ide ]; then
            for x in /sys/bus/ide/devices/*/block; do
                drive=$(basename $(readlink $x));
                $HDPARM -S 0 /dev/$drive
                #$HDPARM -B 255 /dev/$drive
            done
        fi
#       if [ -d /sys/bus/scsi ]; then
#           for x in /sys/bus/scsi/devices/*/block; do
#               drive=$(basename $(readlink $x));
#               $HDPARM -S 0 /dev/$drive
#               #$HDPARM -B 255 /dev/$drive
#           done
#       fi
        $LAPTOP_MODE stop
    fi

    for x in /tmp/.X11-unix/*; do
        displaynum=`echo $x | sed s#/tmp/.X11-unix/X##`
        getXuser;
        if [ x"$XAUTHORITY" != x"" ]; then
            export DISPLAY=":$displaynum"
            su $user -c "xscreensaver-command -unthrottle" &
            xset dpms 0 0 600
        fi
    done
fi

```

---

