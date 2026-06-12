---
title: "Upgrade to 8.10: Bluetooth mouse issue [solution?]"
date: 2008-11-01
forum: Hardware
---

### Post by supercheetah on 2008-11-01
I just solved one of my Bluetooth issues I had when I upgraded from Hardy.

Essentially, I made some customizations to some conf files in /etc to get my Microsoft Bluetooth Notebook Mouse 5000 working, and I am betting that other people made the same kind of customizations because they come from [here](http://www.ubuntugeek.com/howto-setup-bluetooth-keyboard-and-mouse-in-ubuntu.html), and specifically, I made changes to /etc/bluetooth/hcid.conf.

My version of the file had the following added at the end, which was the only change in the file from the default version:
```

device nn:nn:nn:nn:nn:nn {
       name "Microsoft Mouse";
}

```
(nn:nn:nn:nn:nn:nn is where I had my mouse's device address)

Anyway, I removed that line, and I used the Bluetooth Applet to add my mouse, and it worked with no hassle!

So, as a tip, in general, if you made any changes/customizations to anything in /etc in 8.04, and it's not working now, try reverting those changes to their default state.

---

### Post by Harokey on 2008-11-04
I had connected my mouse through the bluetooth manager and it worked for a while. But now I try to connect and have tried to reconnect to the mouse and it just gives me a "Pairing Failed" message.

I tried wiping all the pairing information in /var/lib/bluetooth but that didn't help at all. 

Any Ideas?

Edit: 

I wiped the pairing information in /var/lib/bluetooth and then restarted bluetooth:

sudo /etc/init.d/bluetooth restart

And then run the GUI program to add the device but this is a pain. What has replaced hidd in 8.04 because it is no longer present in 8.10?

---

### Post by lift28 on 2008-11-04
this works until the device goes to sleep then you have to manually reconnect:( waiting .....

---

### Post by peterl on 2008-11-08
> **lift28 said:**
> this works until the device goes to sleep then you have to manually reconnect:( waiting .....

Hello!

I have a similar problem with my ms intellimouse explorer for bluetooth... every now and then it seems to fall asleep, and the led on the bottom goes out completely. I have to press a few of the buttons, which seems to wake it back up and it reconnects. I guess that when I press the buttons it sends a 'look at me i'm a mouse' to the computer, but i don't know why it falls asleep like this in the first place. Could the computer be sending the 'fall asleep' to the mouse?

(you may have guessed i don't really understand how bluetooth works!)

thanks!
Peter. *wakes up mouse to click submit reply*

---

### Post by bigjig on 2008-11-09
hi, just came across this post.. I have a strance problem, the bluetooth mouse works but the scroll doesn't!

Anybody come across this issue? Please help us with a fix..

I use 8.04 Hardy and its a microsoft bluetooth notebook mouse 5000

:confused:

Many thanks.

---

### Post by slogger on 2008-12-18
Is there any solution to this problem of the mouse not pairing?

---

### Post by bigjig on 2008-12-19
Been a while, I gave up! If you find something, please let us know mate. cheers.

---

### Post by IQRules on 2008-12-19
Mine works just fine, RocketFish mouse. 

I have this in /etc/init.d/bluetooth script.

# add by xxx 12/6/2008
**[COLOR="Red"]hciconfig hci0 pscan[/COLOR]**

log_end_msg 0
;;
stop)

---

### Post by bigjig on 2008-12-20
hey thanks for that tip. I am not sure if it has worked for me though! I added those lines at the bottom. 

Do you reckon thats right? Sorry I am really an amateur at all this, just getting to know things at me own pace.



Below is the original bluetooth script file. 

----------------------------------------------------------------------------
#! /bin/sh
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
# LSB 3.0 compilance and enhancements by Filippo Giunchedi <filippo@debian.org>
#
# startup control over dund and pand can be changed by editing
# /etc/default/bluetooth

PATH=/sbin:/bin:/usr/sbin:/usr/bin
DESC=bluetooth

HCID=/usr/sbin/hcid
HCIATTACH=/usr/sbin/hciattach
HCID_NAME=hcid
HCID_OPTIONS="-x -s"

HID2HCI=/usr/sbin/hid2hci
HID2HCI_ENABLED=1

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
	if ! test -x $DUND_DAEMON; then
		DUND_ENABLED=0
	fi
fi

if test "$PAND_ENABLED" != "0"; then
	if ! test -x $PAND_DAEMON; then
		PAND_ENABLED=0
	fi
fi

if test "$HIDD_ENABLED" != "0"; then
	if ! test -x $HIDD_DAEMON; then
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
			if [ "$VERBOSE" != "no" ]; then
				$SDPTOOL $o
			else
				$SDPTOOL $o &>/dev/null 2>&1
			fi
		done
		IFS="$oldifs"
	fi

}

enable_hci_input()
{
       if [ "$VERBOSE" != no ]; then
               log_progress_msg "hid_devices"
               $HID2HCI --tohci
       else
               $HID2HCI --tohci >/dev/null 2>&1
       fi
}

disable_hci_input()
{
       if [ "$VERBOSE" != no ]; then
               log_progress_msg "hid_devices"
               $HID2HCI --tohid
       else
               $HID2HCI --tohid >/dev/null 2>&1
       fi
}

start_pan()
{
	if test "$DUND_ENABLED" != "0"; then
		start-stop-daemon --start --quiet --exec $DUND_DAEMON -- $DUND_OPTIONS
		[ "$VERBOSE" != no ] && log_progress_msg "pand"

	fi
	if test "$PAND_ENABLED" != "0"; then
		start-stop-daemon --start --quiet --exec $PAND_DAEMON -- $PAND_OPTIONS
		[ "$VERBOSE" != no ] && log_progress_msg "pand"
	fi
}


stop_pan()
{
	if test "$DUND_ENABLED" != "0"; then
		start-stop-daemon --stop --quiet --exec $DUND_DAEMON || true
		[ "$VERBOSE" != no ] && log_progress_msg "pand"
	fi
	if test "$PAND_ENABLED" != "0"; then
		start-stop-daemon --stop --quiet --exec $PAND_DAEMON || true
		[ "$VERBOSE" != no ] && log_progress_msg "pand"
	fi
}

start_hid()
{
	if test "$HIDD_ENABLED" != "0"; then
		start-stop-daemon --start --quiet --exec $HIDD_DAEMON -- $HIDD_OPTIONS
		[ "$VERBOSE" != no ] && log_progress_msg "hidd"
	fi
}

stop_hid()
{
	if test "$HIDD_ENABLED" != "0"; then
		$HIDD_DAEMON --killall
		start-stop-daemon --stop --quiet --exec $HIDD_DAEMON || true
		[ "$VERBOSE" != no ] && log_progress_msg "hidd"
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
                       log_progress_msg "rfcomm"
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
                       log_progress_msg "rfcomm"
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
                       log_progress_msg  "rfcomm"
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
	
	if test "$BLUETOOTH_ENABLED" = "0"; then
		log_progress_msg "disabled. see /etc/default/bluetooth"
		log_end_msg 0
		exit 0
	fi

	start-stop-daemon --start --quiet --exec $HCID -- $HCID_OPTIONS || true
	log_progress_msg "hcid"
	
	run_sdptool || true

	start_uarts || true
	
	start_hid || true
	if test "$HID2HCI_ENABLED" = "1"; then
		enable_hci_input || true
	fi
	start_rfcomm || true
	start_pan || true
	log_end_msg 0
    ;;
  stop)
	log_daemon_msg "Stopping $DESC"
	if test "$BLUETOOTH_ENABLED" = "0"; then
		log_progress_msg "disabled."
		log_end_msg 0
		exit 0
	fi
	stop_pan || true
	stop_rfcomm || true
	if test "$HID2HCI_ENABLED" = "1"; then
		disable_hci_input || true
	fi
	stop_hid || true
	start-stop-daemon --stop --quiet --exec $HCID || true
	log_progress_msg "hcid"
	stop_uarts || true
	log_end_msg 0
    ;;
  restart|force-reload)
	log_daemon_msg "Restarting $DESC"
	stop_hid || true
	stop_pan || true
	start-stop-daemon --stop --quiet --exec $HCID || true
	sleep 1
	if test "$BLUETOOTH_ENABLED" = "0"; then
		log_progress_msg "disabled. see /etc/default/bluetooth"
		log_end_msg 0
		exit 0
	fi
	start-stop-daemon --start --quiet --exec $HCID -- $HCID_OPTIONS || true
	log_progress_msg "hcid"
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
--------------------------------------------------------------------------

---

### Post by IQRules on 2008-12-20
start)
log_daemon_msg "Starting $DESC"

if test "$BLUETOOTH_ENABLED" = "0"; then
log_progress_msg "disabled. see /etc/default/bluetooth"
log_end_msg 0
exit 0
fi

start-stop-daemon --start --quiet --exec $HCID -- $HCID_OPTIONS || true
log_progress_msg "hcid"

run_sdptool || true

start_uarts || true

start_hid || true
if test "$HID2HCI_ENABLED" = "1"; then
enable_hci_input || true
fi
start_rfcomm || true
start_pan || true

[B]--- PUT it right here

log_end_msg 0[/B];;
stop)
log_daemon_msg "Stopping $DESC"

And I have this file.

/etc/bluetooth$ cat hcid.conf
device 00:16:38:39:CA:40 {
name "Rocketfish Apple Bluetooth Mouse";
}

---

