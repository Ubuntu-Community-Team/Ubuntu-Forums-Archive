---
title: "[SOLVED] Need Help With toshset"
date: 2007-09-23
forum: Hardware &amp; Laptops
---

### Post by hotweiss on 2007-09-23
According to this site there is a solution to my Bluetooth problem. To have my Bluetooth start automatically started at start up I should follow these instructions:

[http://tegmento-linux.blogspot.com/](http://tegmento-linux.blogspot.com/)

> bluetooth: works. The only problem is that it needs to be enabled via an acpi call. As the toshiba_acpi module does not support bluetooth, other ways have to be found:

    * The simpler method ist by using the toshset tool (install the package toshset) and calling (as root or by sudo) toshset -bluetooth on. I added the lines toshset -bluetooth on and toshset -bluetooth off to the start/stop/restart sections in the /etc/init.d/bluetooth startscript and now bluetooth is automatically recognized on startup.


Now the problem is that I don't know exactly where to place toshset -bluetooth on.

Can some one do this for me:

> #! /bin/bash
### BEGIN INIT INFO
# Provides: bluetooth
# Required-Start:    $local_fs $syslog $remote_fs
# Required-Stop:     $local_fs $syslog $remote_fs
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: Start bluetooth daemons
### END INIT INFO
#
# bluez-utils    Bluetooth subsystem starting and stopping
#
# originally from bluez's scripts/bluetooth.init
#
# Edd Dumbill <ejad@debian.org>
# LSB 3.0 compilance and enhancements  by Filippo Giunchedi <filippo@debian.org>
#
# startup control over dund and pand can be changed by editing
# /etc/default/bluez-utils

PATH=/sbin:/bin:/usr/sbin:/usr/bin
DESC="Bluetooth services"

HCID=/usr/sbin/hcid
HCIATTACH=/usr/sbin/hciattach
HCID_NAME=hcid
HCID_OPTIONS="-x -s"

HID2HCI=/usr/sbin/hid2hci

UART_CONF=/etc/bluetooth/uart

RFCOMM=/usr/bin/rfcomm
RFCOMM_NAME=rfcomm
RFCOMM_CONF=/etc/bluetooth/rfcomm.conf

SDPTOOL=/usr/bin/sdptool

DUND_DAEMON=/usr/bin/dund
DUND_NAME=dund
PAND_DAEMON=/usr/bin/pand
PAND_NAME=pand
HIDD_DAEMON=/usr/bin/hidd
HIDD_NAME=hidd

DUND_ENABLED=0
PAND_ENABLED=0
HIDD_ENABLED=0
DUND_OPTIONS=""
PAND_OPTIONS=""
HIDD_OPTIONS="--master --server"

test -f /etc/default/bluetooth && . /etc/default/bluetooth
test -f /etc/default/rcS && . /etc/default/rcS

. /lib/lsb/init-functions

# test for essential daemons
test -x $HCID || exit 0
test -x $HCIATTACH || exit 0
test -x $RFCOMM || exit 0

# disable nonessential daemons if not present
if test "$DUND_ENABLED" != "0"; then
	if ! test -f $DUND_DAEMON; then
		DUND_ENABLED=0
	fi
fi

if test "$PAND_ENABLED" != "0"; then
	if ! test -f $PAND_DAEMON; then
		PAND_ENABLED=0
	fi
fi

if test "$HIDD_ENABLED" != "0"; then
	if ! test -f $HIDD_DAEMON; then
		HIDD_ENABLED=0
	fi
fi

set -e

run_sdptool()
{
	test -x $SDPTOOL || return 1 

	if ! test -z "$SDPTOOL_OPTIONS" ; then
		oldifs="$IFS"
		IFS=";"
		for o in $SDPTOOL_OPTIONS ; do
			#echo "execing $SDPTOOL $o"
			IFS=" "
			$SDPTOOL $o &>/dev/null
		done
		IFS="$oldifs"
	fi

}

enable_hci_input()
{
       if [ "$VERBOSE" != no ]; then
               log_success_msg "Switching on Bluetooth input devices..."
               $HID2HCI --tohci
       else
               $HID2HCI --tohci >/dev/null 2>&1
       fi
}

disable_hci_input()
{
       if [ "$VERBOSE" != no ]; then
               log_success_msg "Switching Bluetooth input devices back to HID mode..."
               $HID2HCI --tohid
       else
               $HID2HCI --tohid >/dev/null 2>&1
       fi
}

start_pan()
{
	if test "$DUND_ENABLED" != "0"; then
		start-stop-daemon --start --quiet --exec $DUND_DAEMON -- $DUND_OPTIONS
		[ "$VERBOSE" != no ] && log_success_msg "Starting $DUND_NAME..."

	fi
	if test "$PAND_ENABLED" != "0"; then
		start-stop-daemon --start --quiet --exec $PAND_DAEMON -- $PAND_OPTIONS
		[ "$VERBOSE" != no ] && log_success_msg "Starting $PAND_NAME..."
	fi
}


stop_pan()
{
	if test "$DUND_ENABLED" != "0"; then
		start-stop-daemon --stop --quiet --exec $DUND_DAEMON || true
		[ "$VERBOSE" != no ] && log_success_msg "Stopping $DUND_NAME..."
	fi
	if test "$PAND_ENABLED" != "0"; then
		start-stop-daemon --stop --quiet --exec $PAND_DAEMON || true
		[ "$VERBOSE" != no ] && log_success_msg "Stopping $PAND_NAME..."
	fi
}

start_hid()
{
	if test "$HIDD_ENABLED" != "0"; then
		start-stop-daemon --start --quiet --exec $HIDD_DAEMON -- $HIDD_OPTIONS
		[ "$VERBOSE" != no ] && log_success_msg "Starting $HIDD_NAME..."
	fi
}

stop_hid()
{
	if test "$HIDD_ENABLED" != "0"; then
		$HIDD_DAEMON --killall
		start-stop-daemon --stop --quiet --exec $HIDD_DAEMON || true
		[ "$VERBOSE" != no ] && log_success_msg "Stopping $HIDD_NAME..."
	fi
}

start_uarts()
{
	[ -f $HCIATTACH ] && [ -f $UART_CONF ] || return
	grep -v '^#' $UART_CONF | while read i; do
               if [ "$VERBOSE" != no ]; then
                       $HCIATTACH $i
               else
                       $HCIATTACH $i >/dev/null 2>&1
               fi
	done
}

stop_uarts()
{
	killall hciattach > /dev/null 2>&1 || true
}

start_rfcomm()
{
	if [ -x $RFCOMM ] && [ -f $RFCOMM_CONF ] ; then
		# rfcomm must always succeed for now: users
		# may not yet have an rfcomm-enabled kernel
                if [ "$VERBOSE" != no ]; then
                       log_success_msg "Starting $RFCOMM_NAME..."
                       $RFCOMM -f $RFCOMM_CONF bind all || true
                else
                       $RFCOMM -f $RFCOMM_CONF bind all >/dev/null 2>&1 || true
                fi
	fi
}

stop_rfcomm()
{
	if [ -x $RFCOMM ] ; then
               if [ "$VERBOSE" != no ]; then
                       log_success_msg "Stopping $RFCOMM_NAME..."
                       $RFCOMM unbind all || true
               else
                       $RFCOMM unbind all >/dev/null 2>&1 || true
               fi
	fi
}

restart_rfcomm()
{
	if [ -x $RFCOMM ] && [ -f $RFCOMM_CONF ] ; then
               if [ "$VERBOSE" != no ]; then
                       log_success_msg  "Restarting $RFCOMM_NAME..."
                       $RFCOMM unbind all || true
                       $RFCOMM -f $RFCOMM_CONF bind all || true
               else
                       $RFCOMM unbind all >/dev/null 2>&1|| true
                       $RFCOMM -f $RFCOMM_CONF bind all >/dev/null 2>&1 || true
               fi
	fi
}

case "$1" in
  start)
	log_daemon_msg "Starting $DESC"
	
	if test "$BLUETOOTH_ENABLED" == "0"; then
		log_progress_msg "disabled. see /etc/default/bluetooth"
		log_end_msg 0
		exit 0
	fi

	start-stop-daemon --start --quiet --exec $HCID -- $HCID_OPTIONS || true
	log_progress_msg "hcid"
	start_uarts || true
	
	start_hid || true
	enable_hci_input || true
	start_rfcomm || true
	start_pan || true
	log_end_msg 0
    ;;
  stop)
	log_daemon_msg "Stopping $DESC"
	stop_pan || true
	stop_rfcomm || true
	disable_hci_input || true
	stop_hid || true
	start-stop-daemon --stop --quiet --exec $HCID || true
	log_progress_msg "$HCID_NAME"
	stop_uarts || true
	log_end_msg 0
    ;;
  restart|force-reload)
	log_daemon_msg "Restarting $DESC"
	stop_hid || true
	stop_pan || true
	start-stop-daemon --stop --quiet --exec $HCID || true
	sleep 1
	if test "$BLUETOOTH_ENABLED" == "0"; then
		log_progress_msg "disabled. see /etc/default/bluetooth"
		log_end_msg 0
		exit 0
	fi
	start-stop-daemon --start --quiet --exec $HCID -- $HCID_OPTIONS || true
	log_progress_msg "$HCID_NAME"
	start_pan || true
	start_hid || true
	restart_rfcomm
	log_end_msg 0
    ;;
  *)
	N=/etc/init.d/bluetooth
	# echo "Usage: $N {start|stop|restart|reload|force-reload}" >&2
	echo "Usage: $N {start|stop|restart|force-reload}" >&2
	exit 1
	;;
esac

exit 0

# vim:noet

Thanks.

---

### Post by hotweiss on 2007-09-24
OK, I found a solution at Tim Anderson's blog:

[http://www.itwriting.com/blog/?p=333#comment-35858](http://www.itwriting.com/blog/?p=333#comment-35858)

---

### Post by SpiritIsReality on 2007-09-25
howdy
cool...thanks
now they say, if you click on the thread tools, and mark it solved, then others that
search for bluetooth in posts, or toshset in titles...on the advanced search. and look for
threads marked solved,  could find an answer to their problems.

usually it's somebody else that answers the op's question. way to go. good find.
how'd you find it anyway. a search you could post here maybe?

trails

---

