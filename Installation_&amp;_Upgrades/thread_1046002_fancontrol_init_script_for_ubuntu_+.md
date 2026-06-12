---
title: "fancontrol init script for ubuntu +"
date: 2009-01-21
forum: Installation &amp; Upgrades
---

### Post by catkin on 2009-01-21
[FONT="Arial"]Hello  :-)

Here's a standards-compliant init script for fancontrol, developed and tested using fancontrol 0.66 on ubuntu 8.04.1. It may work on other ubuntus, debian and other debian-based systems using lsb-base (>= 3.0-6).

Part of the standards-compliance is that the script issues no messages at boot or shutdown if /etc/default/rcS has VERBOSE=no (the default value)

The init script can be installed issuing the following command (with root privileges)

[FONT="Courier New"][SIZE="2"]update-rc.d fancontrol defaults 99 01[/SIZE][/FONT]

BTW, pwmconfig from the current ubuntu lm-sensors package (1:3.0.0-4ubuntu2) does not set START and STOP values; use the version from the 3.0.3 package.[/FONT]
```

#! /bin/sh

# fancontrol startup script

# fancontrol is part of the lm-sensors package

# Developed and tested using fancontrol 0.66 on ubuntu 8.04.1; may work
# on other ubuntus, debian and other debian-based systems using 
# lsb-base (>= 3.0-6)

# INIT INFO for insserv and YaST
### BEGIN INIT INFO
# Provides:          fancontrol
# Required-Start:    $local_fs
# Required-Stop:
# Default-Start:     2 3 4 5
# Default-Stop:      S 0 1 6
# Short-Description: fancontrol
# Description:       fan control
### END INIT INFO

# Change History
#   20jan09 Charles
#       * Creation on ubuntu 8.04.1 with lm-sensors 1:3.0.0-4ubuntu2, 
#         using skeleton 1.8 as a pro-forma with minimal functional change

# PATH is not set because no reason to change what init provides
DESC="fan controller"
NAME=fancontrol
DAEMON=/usr/sbin/$NAME
DAEMON_ARGS=
PIDFILE=/var/run/$NAME.pid
SCRIPTNAME=/etc/init.d/$NAME

# Exit if the package is not installed
[ -x "$DAEMON" ] || exit 0

# Read configuration variable file if it is present
[ -r /etc/default/$NAME ] && . /etc/default/$NAME

# Load the VERBOSE setting and other rcS variables
[ -f /etc/default/rcS ] && . /etc/default/rcS

# Define LSB log_* functions.
# Depend on lsb-base (>= 3.0-6) to ensure that this file is present.
. /lib/lsb/init-functions

#
# Function that starts the daemon/service
#
# fancontrol does not background itself so start-stop-daemon's -b option used
do_start()
{
	# Return
	#   0 if daemon has been started
	#   1 if daemon was already running
	#   2 if daemon could not be started
	start-stop-daemon -b --start --quiet --pidfile $PIDFILE --exec $DAEMON --test > /dev/null \
		|| return 1
	start-stop-daemon -b --start --quiet --pidfile $PIDFILE --exec $DAEMON -- \
		$DAEMON_ARGS \
		|| return 2
}

#
# Function that stops the daemon/service
#
do_stop()
{
	# Return
	#   0 if daemon has been stopped
	#   1 if daemon was already stopped
	#   2 if daemon could not be stopped
	#   other if a failure occurred
	start-stop-daemon --stop --quiet --retry=TERM/30/KILL/5 --pidfile $PIDFILE --name $NAME
	RETVAL="$?"
	[ "$RETVAL" = 2 ] && return 2
	# Many daemons don't delete their pidfiles when they exit.
	rm -f $PIDFILE
	return "$RETVAL"
}

case "$1" in
  start)
	[ "$VERBOSE" != no ] && log_daemon_msg "Starting $DESC" "$NAME"
	do_start
	case "$?" in
		0|1) [ "$VERBOSE" != no ] && log_end_msg 0 ;;
		2) [ "$VERBOSE" != no ] && log_end_msg 1 ;;
	esac
	;;
  stop)
	[ "$VERBOSE" != no ] && log_daemon_msg "Stopping $DESC" "$NAME"
	do_stop
	case "$?" in
		0|1) [ "$VERBOSE" != no ] && log_end_msg 0 ;;
		2) [ "$VERBOSE" != no ] && log_end_msg 1 ;;
	esac
	;;
  restart|force-reload)
	log_daemon_msg "Restarting $DESC" "$NAME"
	do_stop
	case "$?" in
	  0|1)
		do_start
		case "$?" in
			0) log_end_msg 0 ;;
			1) log_end_msg 1 ;; # Old process is still running
			*) log_end_msg 1 ;; # Failed to start
		esac
		;;
	  *)
	  	# Failed to stop
		log_end_msg 1
		;;
	esac
	;;
  *)
	echo "Usage: $SCRIPTNAME {start|stop|restart|force-reload}" >&2
	exit 3
	;;
esac
```

---

