---
title: "HOWTO: Bluetooth Keyboard and Mouse"
date: 2006-08-01
forum: Hardware &amp; Laptops
---

### Post by boneill on 2006-08-01
I have a [Microsoft Optical Desktop Elite for Bluetooth](http://www.microsoft.com/uk/hardware/mouseandkeyboard/productdetails.aspx?pid=033) and I use Ubuntu. This tutorial should help you getting your keyboard and mouse up and running (and automatically reconnecting after you reboot, idle, or whatever).

This tutorial is an adapted version of [this forum thread](http://www.ubuntuforums.org/showthread.php?t=224673) by naag.

[size=+1]Getting Started[/size]

We need the MAC address (e.g. 00:00:00:00:00) of the mouse and keyboard. I shall use *KEYBOARD_ADDR* and *MOUSE_ADDR* where you should find the addresses for the keyboard and mouse respectively. Press the button on the mouse that makes it visible to be found by the computer. Do the same for the keyboard. Now open a terminal window and run the following command:

```

 user@computer:~$ hcitool scan
 Scanning ...
         KEYBOARD_ADDR       Microsoft Wireless Keyboard
         MOUSE_ADDR          Microsoft Mouse
 user@computer:~$
```

[size=+1]Adding the Keyboard and Mouse[/size]

Now we need to add the keyboard and mouse to the bluetooth configuration files. Run the following command to pop up GEdit:

```

 user@computer:~$ sudo gedit /etc/bluetooth/hcid.conf
```

You may be asked for your password, this is because we used *sudo*.

At the end of the file, add the following (replacing KEYBOARD_ADDR and MOUSE_ADDR for the keyboard and mouse MAC addresses as found earlier):

```

 device KEYBOARD_ADDR {
     name "Microsoft Wireless Keyboard";
     auth enable;
     encrypt enable;
 }
 
 device MOUSE_ADDR {
     name "Microsoft Mouse";
 }
```

Now you need to restart the bluetooth subsystem so that it refreshes it's configuration file.

```

 user@computer:~$ sudo /etc/init.d/bluez-utils restart
  * Restarting Bluetooth services... [ ok ]
```

[size=+1]Pairing the Devices[/size]

You now need to pair the devices with the computer. Do not press any buttons on the keyboard as we'll need to use it to enter a passcode so we can pair. Run the following command:

```

 user@computer:~$ sudo hidd --search
 Searching ...
         Connecting to device MOUSE_ADDR
         Connecting to device KEYBOARD_ADDR
 user@computer:~$
```

They could pair with the computer in any order, you will need to remember which one is the keyboard. As soon as *Connecting to device KEYBOARD_ADDR* appears you must enter a PIN code into the keyboard. It must consist of numbers **not using the numpad**, I can't remember how many you can use, but somewhere between 4 and 8 should be fine. Type this number in to the keyboard and press *Return*.

A window should pop up on your computer asking you for the number you just entered on the keyboard.

You should now be set up. The devices should automatically reconnect when they go to sleep and when your computer boots up.

[size=+1]Troubleshooting[/size]

If you have followed all the steps above and you find your mouse or keyboard don't automatically reconnect, we can fix it! I had to do this to get mine to work. Run the following command in a terminal:

```

 user@computer:~$ sudo gedit /etc/default/bluez-utils
```

Find the lines with the following:

```

 HIDD_ENABLED=0
 HIDD_OPTIONS="..."
```

Change them to:

```

 HIDD_ENABLED=1
 HIDD_OPTIONS="--master --connect KEYBOARD_ADDR --connect MOUSE_ADDR --server"
```

Now reboot and hopefully they'll automatically connect (give them a few seconds to connect after you move the mouse/press a key).

[size=+1]See Also[/size]

* [HOWTO: Apple Wireless Keyboard (Ubuntu Forums)](http://www.ubuntuforums.org/showthread.php?t=224673)
* [Bluetooth mouse (Ubuntu Forums)](http://www.ubuntuforums.org/showthread.php?t=87919)

---

### Post by naag on 2006-08-01
This is a nice summary of the other threads. Most people should get those bluetooth devices working now :-)

---

### Post by laughterwym on 2006-08-02
i have my lovely mouse go now. thankx

---

### Post by lenticular on 2006-08-05
Thanks,is a big help.  I've got my Logitech BT Dinovo up and running.

---

### Post by x64Jimbo on 2006-08-09
Whenever I try to get my keyboard to connect after following your instructions, all I get is an LMP Timeout error. What am I doing wrong?

---

### Post by AusIV4 on 2006-12-02
I realize this thread is a bit old, but I've followed the instructions and I'm having problems.

I switched my laptop from Windows to Ubuntu today, and my mouse is the biggest problem I'm having (so far). I'm running Dapper for the LTS, if there have been any changes in edgy.

Here's the thing: when I turn my mouse on and back off, it takes a long time for my mouse to reconnect. It seems as though my mouse has to go to sleep (I believe 15 seconds of inactivity) then be moved, and it will reconnect. It could certainly be worse, but I try to do everything I can to extend the battery life of my mice, and I don't particularly want to have to wait 15 seconds every time I need to turn my mouse back on.

If there's no good solution, maybe I'll just invest in a battery recharger and some rechargeable batteries, so I don't have to worry about it.

---

### Post by optimarcus_prime on 2007-01-15
Thank you for this guide, it has worked beautifully.  However, I am still having an issue.

I can pair my mouse [Targus laser Bluetooth rechargable mouse], and it works properly, but I am still having the issue that you had where you can't get the mouse to reconnect after the computer/mouse sleeps.  I've tried using your method of editing /etc/default/bluez-utils, but my problem is that I can't find this file anywhere.  When I run this command, ubuntu attempts to create a new file, which I don't want.  Can someone help me with this issue?  I've installed and reinstalled bluez-utils several times, and still the file is non-existant.

---

### Post by optimarcus_prime on 2007-01-24
i've got my mouse working on a manual connect, but I still can't get it to work automatically.  This is my /etc/init.d/bluetooth file:
```
#! /bin/bash
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
HCID_OPTIONS=-x

HID2HCI=/usr/sbin/hid2hci

UART_CONF=/etc/bluetooth/uart

RFCOMM=/usr/bin/rfcomm
RFCOMM_NAME=rfcomm
RFCOMM_CONF=/etc/bluetooth/rfcomm.conf

SDPD=/usr/sbin/sdpd
SDPD_NAME=sdpd

SDPTOOL=/usr/bin/sdptool

DUND_DAEMON=/usr/bin/dund
DUND_NAME=dund
PAND_DAEMON=/usr/bin/pand
PAND_NAME=pand
HIDD_DAEMON=/usr/bin/hidd
HIDD_NAME=hidd

DUND_ENABLED=0
PAND_ENABLED=0
#HIDD_ENABLED=0
HIDD_ENABLED=1
DUND_OPTIONS=""
PAND_OPTIONS=""
#HIDD_OPTIONS="--master --server"
HIDD_OPTIONS="--master --connect 00:12:A1:60:2D:9D --server"

test -f /etc/default/bluetooth && . /etc/default/bluetooth
test -f /etc/default/rcS && . /etc/default/rcS

. /lib/lsb/init-functions

# test for essential daemons
test -x $HCID || exit 0
test -x $HCIATTACH || exit 0
test -x $RFCOMM || exit 0
test -x $SDPD || exit 0

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
	
	start-stop-daemon --start --quiet --exec $SDPD || true
	log_progress_msg "sdpd"
    
	run_sdptool || true
	log_progress_msg "sdp_options"

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
	start-stop-daemon --stop --quiet --exec $SDPD || true
	log_progress_msg "$SDPD_NAME"
	start-stop-daemon --stop --quiet --exec $HCID || true
	log_progress_msg "$HCID_NAME"
	stop_uarts || true
	log_end_msg 0
    ;;
  restart|force-reload)
	log_daemon_msg "Restarting $DESC"
	stop_hid || true
	stop_pan || true
	start-stop-daemon --stop --quiet --exec $SDPD || true
	start-stop-daemon --stop --quiet --exec $HCID || true
	sleep 1
	if test "$BLUETOOTH_ENABLED" == "0"; then
		log_progress_msg "disabled. see /etc/default/bluetooth"
		log_end_msg 0
		exit 0
	fi
	start-stop-daemon --start --quiet --exec $HCID -- $HCID_OPTIONS || true
	start-stop-daemon --start --quiet --exec $SDPD || true
	log_progress_msg "$HCID_NAME"
	log_progress_msg "$SDPD_NAME"
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

```

any suggestions?

---

### Post by optimarcus_prime on 2007-01-25
Ah, nevermind.  I got it to work.  Thanks for the great howto.

---

### Post by x64Jimbo on 2007-02-01
Ok so I recently upgraded to the Elite (Bluetooth 2.0) and I am impressed with the feel of the keyboard and mouse. However. I am getting some very strange behavior from the mouse. The pointer is very inaccurate on the screen. When going very slowly over the surface of my desk or any other surface, the pointer bounces around and doesn't maintain a straight line. These are the very same surfaces that have been working fine with two other Intellimouse models, including one from the first generation MS Bluetooth combo set. Is there something different about the Elite mouse's optical eye that I should know about? I love how it feels, but it's nearly unusable this way.

Edit: The twitchiness/jumpiness of the cursor only exists when there is an active window manager. (Kwin and Beryl both exhibit the problem) When only KDM is loaded, the mouse is precise and smooth. I tried playing around with the Option Resolution "#" in xorg.conf, but that hasn't seemed to change anything. What's different about how a mouse is read as an input between the time when I'm logging in with the KDM greeter and the time I reach my desktop?

As a side note, I would like to get the bonus buttons on the keyboard and mouse working... Especially the back/forward buttons. Any ideas about how to do that?

---

### Post by dans on 2007-02-13
My bluetooth mouse seems to go to sleep every so often.  This happens every 30 sec to 2 min.  I'll be off the mouse typing for a while then when I grab the mouse there is no pointer response.  I jiggle for 2 to 5 sec and then the pointer starts responding.  This doesn't happen every time I'm off the mouse, but does seem to happen most times I'm off the mouse for more than a few sec.

Any ideas on how to fix this?

Specs:
*  Ubuntu Edgy
*  Dell Inspiron 6000 w/ built-in b/t
*  Logitech b/t mouse

---

### Post by Kenja on 2007-02-20
It seems that my MX900 doesn't like to connect on startup all the time.  Occasionally it works but I have to click the mouse buttons like mad for it to recognize it before login.

I can make it work by using
```
sudo /etc/init.d/bluetooth restart
```

My /etc/init.d/bluetooth
```
#! /bin/bash
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
HCID_OPTIONS=-x

HID2HCI=/usr/sbin/hid2hci

UART_CONF=/etc/bluetooth/uart

RFCOMM=/usr/bin/rfcomm
RFCOMM_NAME=rfcomm
RFCOMM_CONF=/etc/bluetooth/rfcomm.conf

SDPD=/usr/sbin/sdpd
SDPD_NAME=sdpd

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
test -x $SDPD || exit 0

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
	
	start-stop-daemon --start --quiet --exec $SDPD || true
	log_progress_msg "sdpd"
    
	run_sdptool || true
	log_progress_msg "sdp_options"

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
	start-stop-daemon --stop --quiet --exec $SDPD || true
	log_progress_msg "$SDPD_NAME"
	start-stop-daemon --stop --quiet --exec $HCID || true
	log_progress_msg "$HCID_NAME"
	stop_uarts || true
	log_end_msg 0
    ;;
  restart|force-reload)
	log_daemon_msg "Restarting $DESC"
	stop_hid || true
	stop_pan || true
	start-stop-daemon --stop --quiet --exec $SDPD || true
	start-stop-daemon --stop --quiet --exec $HCID || true
	sleep 1
	if test "$BLUETOOTH_ENABLED" == "0"; then
		log_progress_msg "disabled. see /etc/default/bluetooth"
		log_end_msg 0
		exit 0
	fi
	start-stop-daemon --start --quiet --exec $HCID -- $HCID_OPTIONS || true
	start-stop-daemon --start --quiet --exec $SDPD || true
	log_progress_msg "$HCID_NAME"
	log_progress_msg "$SDPD_NAME"
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

```

---

### Post by stego_s_aurus on 2007-02-23
WOOT!
  These instructions ALSO works for a WACOM Graphire Bluetooth Tablet!! (model CTE-630BT)

---

### Post by Icarus3000 on 2007-02-25
> **optimarcus_prime said:**
> Ah, nevermind.  I got it to work.  Thanks for the great howto.

I am having the same problem you were having - mouse connects manually, but not after sleeping.  I also have no "bluez-util" file to modify.

What did you do to get it to work?

Thanks!
Icarus3000

---

### Post by alex_mayorga on 2007-02-26
This guide helped me regain my Logitech diNovo Media Desktop Laser on Feisty I only had to use a small variation of the commands as follows:

sudo gedit /etc/bluetooth/hcid.conf

sudo /etc/init.d/bluetooth restart

Thank you very much on sharing this insight.

---

### Post by dnns on 2007-03-05
Could you elaborate alex_mayorga? I've been trying to follow this guide with the same Logitech diNovo desktop set but the only way I can get my k/b and mouse working is if I turn my bluetooth services off. In bluetooth discoverable mode they aren't recognized.

---

### Post by alex_mayorga on 2007-03-21
> **dnns said:**
> Could you elaborate alex_mayorga? I've been trying to follow this guide with the same Logitech diNovo desktop set but the only way I can get my k/b and mouse working is if I turn my bluetooth services off. In bluetooth discoverable mode they aren't recognized.

Here's what worked for me:

Press the red buttons on all the pieces of your diNovo set (Keyboard, Mediapad and Mouse) and then run the following command:

```

user@computer:~$ hcitool scan
Scanning ...
        KEYBOARD_ADDR       Logitech diNovo Keyboard
        MEDIAPAD_ADDR       Logitech Mediapad
        MOUSE_ADDR          Logitech MX1000 mouse

```

Gather the addresses of the devices, you can skip the search if you will given that Logitech puts handy stickers with the bluetooth addresses in every piece.

Run this command:
```

user@computer:~$ sudo gedit /etc/bluetooth/hcid.conf
```

Append the following replacing the corresponding bluetooth addresses:
```

device KEYBOARD_ADDR {
	name "Logitech diNovo Keyboard";
	auth enable;
	encrypt enable;
}

device MEDIAPAD_ADDR {
	name "Logitech Mediapad";
	auth enable;
	encrypt enable;
}

device MOUSE_ADDR {
	name "Logitech MX1000 mouse";
}
``` 

Restart the bluetooth daemon:
```

user@computer:~$ sudo /etc/init.d/bluetooth restart
* Restarting Bluetooth services                                     [ OK ]

```

Proceed to pair the devices, I don't remember exactly the procedure to pair the Keyboard and the Mediapad, please refer to the first post on this thread.
The command to use is like this:
```

user@computer:~$ sudo hidd --search
Searching ...
        Connecting to device KEYBOARD_ADDR
        Connecting to device MEDIAPAD_ADDR
        Connecting to device MOUSE_ADDR

```

Now to make sure the Logitech diNovo Laser set connects on every restart run this command:
```

user@computer:~$ sudo gedit /etc/default/bluetooth

```

Edit this section as shown in **bold** below:
```

############ HIDD
#
# To have Bluetooth mouse and keyboard support, get the
# Linux 2.6.6 patch or better from bluez.org, and set 
# HIDD_ENABLED to 1.
HIDD_ENABLED=**1**
HIDD_OPTIONS="--master **--connect KEYBOARD_ADDR --connect MEDIAPAD_ADDR --connect MOUSE_ADDR** --server"

```

That should do it, this worked for me on Feisty herd 5.
Sorry if it's a repost, it's mainly for my own reference. Hope you get it working dnns.

---

### Post by dnns on 2007-03-29
Thanks a lot for the comprehensive reply alex_mayorga! With your help i have no trouble with my dinovo set at all. Again, many thanks

Now if i could only get my Logitech Bluetooth headset to work with Skype then I'll be a 100% ex-windows user.

---

### Post by mlwollman on 2007-03-31
Hello,

First this HOWTO is great and easy to understand. I got my Logitech Cordless Elite Keyboard and Mouse both working fine, in gdm and gnome. However, it was previously working in grub, and after following these instructions it no longer works in grub. any ideas? I'm using Edgy.

Thank You

---

### Post by painterh on 2007-04-02
Hi;  I am new to Ubuntu, and also have a Microsoft Bluetooth elite desktop mouse and keyboard.  Thanks for the very helpful information regarding getting them to work.  I was able to get my mouse and keyboard recognized and connected using the steps described.  However whenever my system is idle and goes to screen saver, they loose connection.  I can do the "hidd --search command and they reconnect, but I' am afraid I may have screwed something up by opening the bluez-utils/conf file to edit it because  for some reason when I open it now it is empty.   Any help is appreciated.  I am a proficient Windows user but a noob to linux, so any help needs to be fairly detailed.

---

### Post by mtron on 2007-04-10
Nice Collection, thanks.

One thing left to do is to map the multimedia buttons of the MS - Keyboard to functions in xorg. Sb. got this working till now?

cheers

---

### Post by dnns on 2007-04-20
alexmayorga, i forgot t thank you, your guide works perfectly

---

### Post by Brendt2 on 2007-04-23
For some reason HCITOOL SCAN indicates that I have no such device.   Not good says I.

---

### Post by undertakingyou on 2007-04-24
I just upgraded to feisty fawn and am having the same issue.  hcitool scan says no devices.  There is no bluez-utils in the init.d folder.  It is just bluetooth.  I just looked on the bottom of the device where it gives the BlueTooth address and tried that in the different conf files but to no avail.  Still no bluetooth service after reboot.  The bios sees it, the grub menu sees it, not the startup/login screen.  Strange thing, it worked fine all on its own in Edgy, doesn't in Feisty.  Any thoughts?

---

### Post by The Shaolin on 2007-04-24
I'm running Feisty as well...I got it to find the physical addresses of both my keyboard and mouse, I changed the config file, but when I try to restart the bluetooth system, I get:

theshaolin@theshaolin:~$ sudo /etc/init.d/bluez-utils restart
sudo: /etc/init.d/bluez-utils: command not found

Will restarting X do the same thing?

---

### Post by undertakingyou on 2007-04-24
It seems that feisty changed the file from bluez-utils to bluetooth so ```
sudo /etc/init.d/bluetooth restart
``` will restart the bluetooth service.

That being said.  I still can't get it to display the address of my devices and even though I edited the config files it still isn't recongnized on restart.  Any thoughts?  Anyone?

---

### Post by The Shaolin on 2007-04-25
> **undertakingyou said:**
> It seems that feisty changed the file from bluez-utils to bluetooth so ```
sudo /etc/init.d/bluetooth restart
``` will restart the bluetooth service.

That being said.  I still can't get it to display the address of my devices and even though I edited the config files it still isn't recongnized on restart.  Any thoughts?  Anyone?


Ah, that did it!  You also (obviously) have to change the code in the last step.  

Works great, thank you so much for the tutorial!

I copied and pasted the last line of code using my mouse...and I didn't think it worked, I missed the pin number...so I went back to do it again, and I hit enter on the bluetooth keyboard by accident....

and it was like...

...

oh...wait, that shouldn't have worked...lol

---

### Post by yaidiot! on 2007-05-06
@undertaking,

I had similar trouble. Try adding your mouse info to /etc/default/bluetooth:
HIDD_ENABLED=1
HIDD_OPTIONS="-i hci0 --connect XX:XX:XX:XX:XX:XX --master --server"

save, restart bluetooth. Works?

---

### Post by alex_mayorga on 2007-05-22
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/bluez-utils/+bug/32415](https://bugs.launchpad.net/ubuntu/+source/bluez-utils/+bug/32415) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				> **dnns said:**
> alexmayorga, i forgot t thank you, your guide works perfectly
Glad it worked for you :D

I'm linking a bug that seems related in the hopes this could help someone else.

---

### Post by Zhor on 2007-07-24
Thanks for the guide!  I just switched to kubuntu, had used FC4 but didn't like it very well.  I've been using my laptop keyboard and a usb mouse for three days trying to figure the bluetooth out!  It works very well now with my Logitech Cordless Elite Keyboard/Mouse.  I figured out how to restart the Bluetooth service in Feisty, then noticed it was already posted further down.  Helps to read everyone's posts! :lolflag:  Thanks again.

---

### Post by dnns on 2007-08-19
I'm trying out Gutsy these days, and I can say for a fact that the only thing you need to do to get your Logitech diNovo Desktop running in Ubuntu 7.10 is to edit your

gksudo gedit /etc/default/bluetooth

and make sure to enable HIDD and add the addresses of your peripherals:

HIDD_ENABLED=1
HIDD_OPTIONS="--master --connect MOUSE_ADDRESS --connect KEYB_ADDRESS --connect MEDIAPAD_ADDRESS --server"

Finally no need for a backup corded keyboard at login!

---

### Post by redfox314 on 2007-09-01
For anyone who gets 'No such device' when doing 

hcitool scan

I got that when i unplugged and replugged my bluetooth reciever at login to enter my password.

The easiest is to just plugin a spare wired keyboard to do the configuration.

I suppose you could also do the configuration without a working bluetooth adaptor. 
In many cases you don't need to scan for the Bluetooth address it is simply printed on the bottom of the device. (It is with my MX5000 laser set).
So theoretically you could just set the hcid.conf file and the /etc/default/bluetooth or /etc/default/bluez-utils file and reboot.

---

### Post by alex_mayorga on 2007-09-14
**This post could be related to an Ubuntu bug filed at**: [https://bugs.edge.launchpad.net/bluez-utils/+bug/123920](https://bugs.edge.launchpad.net/bluez-utils/+bug/123920) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				> **dnns said:**
> I'm trying out Gutsy these days, and I can say for a fact that the only thing you need to do to get your Logitech diNovo Desktop running in Ubuntu 7.10 is to edit your

gksudo gedit /etc/default/bluetooth

and make sure to enable HIDD and add the addresses of your peripherals:

HIDD_ENABLED=1
HIDD_OPTIONS="--master --connect MOUSE_ADDRESS --connect KEYB_ADDRESS --connect MEDIAPAD_ADDRESS --server"

Finally no need for a backup corded keyboard at login!

dnns,

unfortunately your suggestion is not working for me. Can you please join the fray on chasing Bug #123920 please?

Thanks in advance

---

### Post by Caseyjp on 2007-09-14
Curious that even with Gutsy on boot, USB external devices have such a hard time.

On my box, logitech bluetooth keyboard and mouse won't work until after I get to a login screen...AND pull the bluetooth adapter OUT and put it back in.

The external USB creative sblive?  Same thing.

Guess what?  On the exact SAME hardware, a "clean" install of Debian Etch picks up ALL of these devices and they JUST WORK.

Kinda' scratching my head here, as ubuntu is supposed to be the "newer user" friendly distro, but the "parent" (debian) seems to be the clear winner for these types of devices.

Fiesty has the same issues dealing with bluetooth keyboard/mouse/ creative external, so this isnt' some new "beta" issue.

I've been an Ubuntu user for quite a long time, but this type of oversight strikes me as an 'oops'.

--The hardware isn't even new or "non-supported":

xp2400
ide 80gig wd hdd
1gig ram
fx5200 nvidia  128meg 
creative sblive! external usb
logitech keyboard/mouse (razor) bluetooth. (not the dinovo).

I'm not asking for troubleshooting here.  As debian etch picks these devices up without going through hoops (at all), my concern is that ubuntu does not without either going through CLI hoops, or manual unplug > replug.

---

### Post by alex_mayorga on 2007-09-24
Caseyjp,

Fair enough, thanks on sharing your experience, maybe it's time for me to go "upstream" :)

The diNovo set is the fancier my hardware gets and it's the only still "broken" on Gutsy.

---

### Post by Endolith on 2007-09-27
Is there a way to do this without using the command line?  There's a bluez-gnome package and a gnome-bluetooth package, for instance.

(I'm really sick of rubbing sticks together.)

---

### Post by KevNice on 2007-10-30
thanks for this guide! I didn't have the bluez- package, but the command on the 2nd page for restarting bluetooth did the trick for me

---

### Post by KevNice on 2007-10-31
now i am having the same problem some others are having-- namely, if my computer goes idle or whatever, the connection goes away and I have to punch in the commands again. Its not a big deal, just annoying. Any fix for this? or is there any way I can make some kind of terminal script at startup so it does this automatically when I turn on the PC?

---

### Post by painterh on 2007-10-31
Hi;  I want to thank you for the great info.  It helped me get my Microsoft bluetooth "Elite" mouse and keyboard working.  I just have one issue.  I have a dual boot system with XP and Gutsy.  When I restart from windows to gutsy my bluetooth requires hidd --search before it connects, but when I restart from gutsy back into gutsy, I have connectivity even though it may take several minutes.  Any Ideas? Anyone.

---

### Post by londoner on 2007-11-02
***bump***

I am On gutsy did all the configurations, and I still have to plug and unplug the logitech mouse and keyboard to get any results.

I think this is a bug on feisty.

---

### Post by justDIY on 2007-11-14
my mouse will not auto-reconnect on reboots...

It's a cheapo logitech v470, and it works fine if I do a manual connection.  However, when I restart, I need to preform these steps.  Yes, I've edited the hcid.conf file and the default/bluetooth file already.

$ sudo /etc/init.d/bluetooth stop

now, press the connect button on the underside of the mouse

$ sudo /etc/init.d/bluetooth start

presto mouse works fine

Also the bluetooth service causes my laptop to hang slightly during boot, like it is searching for my mouse.

Is there any way to make it work, without having to hit the connect button every time?

I'm using Fiesty 32 bit on a Compaq nc6320 laptop.

---

### Post by bernardfrancois on 2008-01-12
Thanks for the howto. It worked with my 'Dell BT Keyboard' and 'Dell BT Mouse' (these are the names **hcitool scan** displayed).

Now I have the problem that I can't use the keyboard in grub.

I found a post about it, I'll post something there if I found a solution:
[http://ubuntuforums.org/showthread.php?t=312865&highlight=grub+bluetooth&page=2](http://ubuntuforums.org/showthread.php?t=312865&highlight=grub+bluetooth&page=2)

[edit]
[INDENT]I only had 3 seconds to make a choice in grub, which was not enough to detect the keyboard. Now I changed it to 15 seconds, and it works now. Sometimes I do have to press the button on the back of the keyboard to make it work though.

Sometimes the keyboard and/or mouse doesn't work at the login screen, but this can be solved by unplugging / plugging the bluetooth usb key I'm using.[/INDENT]
[/edit]

---

### Post by caish5 on 2008-01-27
I've tried this solution and can get it to work with my DiNovo desktop. But usually a reboot will kill it and i'll need to do an unplug/replug and another reboot to get it working.

Anyone know how to make it stick?

---

### Post by fraserj on 2008-05-04
THERE'S A SOLUTION TO THE LOGITECH DINOVO BLUETOOTH KEYBOARD/MOUSE PROBLEM!

Does it freeze at the login screen? [Try this.]("http://ubuntuforums.org/showpost.php?p=4806028&postcount=7")

per [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=355497](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=355497)

Type this command in a terminal:
sudo gedit /etc/default/bluetooth

Then look for the line that says:
HID2HCI_ENABLED=1

and change it to this:
HID2HCI_ENABLED=0

---

### Post by JeppeM on 2008-05-14
Are there any issues with doing this stuff, then then sometimes not having the keyboard/mouse present?

I'm considering getting a BT keyboard/mouse for my workstation, but then i take my laptop home, i don't have the keyboard/mouse. I will still be able to use my laptop-keyboard and touchpad, right? :)

---

### Post by caelcynndarr on 2008-05-18
i am having a problem please help !!!! 
thank you 

dylan@laptop:~$ hcitool scan
Device is not available: No such device
dylan@laptop:~$

---

### Post by jason0x21 on 2008-06-23
It's still not working for me.  I have to re-pair every time I reboot.  I've added the right addresses into /etc/bluetooth/hcid.conf...
```
device 00:07:61:B1:81:F6 {
    name "Dell BT Keyboard";
    auth enable;
    encrypt enable;
}
 
device 00:07:61:B1:C2:98 {
    name "Dell BT Mouse";
}

```
...I've made the changes to /etc/default/bluetooth...
```

HID2HCI_ENABLED=0
HIDD_ENABLED=1
HIDD_OPTIONS="-i hci0 --master --connect 00:07:61:b1:c2:98 --connect 00:07:61:b2
:81:f6 --server"

```
...I've even tried the custom init.d script mentioned earlier in this thread.  Nothing seems to work.  Every time I reboot, I have to re-pair on the command line after I log in.
```

sudo hidd --search

```
...which is, to put it mildly, beyond lame.  My hardware is a Dell Precision M4300 laptop with an internal USB bluetooth dongle (no unplugging and replugging there), and my wireless mouse and keyboard are also by dell and work fine with no problems under Windows.  What am I doing wrong here?

---

### Post by jason0x21 on 2008-06-26
The bug that seems to be affecting me is this one here, and the fix (which seems to work) is detailed in the bug report.

[https://bugs.launchpad.net/ubuntu/+source/gnome-bluetooth/+bug/79394](https://bugs.launchpad.net/ubuntu/+source/gnome-bluetooth/+bug/79394)

---

