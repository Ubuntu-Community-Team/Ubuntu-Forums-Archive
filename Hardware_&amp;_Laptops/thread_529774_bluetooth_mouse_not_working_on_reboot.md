---
title: "bluetooth mouse not working on reboot"
date: 2007-08-19
forum: Hardware &amp; Laptops
---

### Post by abadfish on 2007-08-19
computer:  Dell Dimension D830 laptop
mouse:  bluetooth Mogo mouse

I'm able to get my bluetooth mouse to work when I pair it with my laptop.  So I know the mouse is working.  However, when I boot my laptop, I have to pair it again in order to get the mouse to work.

I've tried all the suggestions mentioned in other threads:
[http://ubuntuforums.org/showthread.php?t=87919&highlight=mogo](http://ubuntuforums.org/showthread.php?t=87919&highlight=mogo)
[http://ubuntuforums.org/showthread.php?t=227057&highlight=bluetooth+mouse](http://ubuntuforums.org/showthread.php?t=227057&highlight=bluetooth+mouse)

But I've been unsuccessful.  One thing I did notice that is different though is when I try to restart the bluetooth services.  Here is what happens:

```

 % sudo /etc/init.d/bluetooth restart
 * Restarting Bluetooth services                                                Can't get device information: Host is down
                                                                         [ OK ]
% 

```

I'm assuming this is the crux of my problem since everyone else is getting the services to restart fine.

Any ideas why I can't get this service to restart???

If it helps here is my /etc/default/bluetooth file:
```

# Defaults for bluez-utils

# This file supersedes /etc/default/bluez-pan.  If
# that exists on your system, you should use this
# file instead and remove the old one.  Until you
# do so, the contents of this file will be ignored.

# start bluetooth on boot?
# compatibility note: If this variable is not found bluetooth will
# start
BLUETOOTH_ENABLED=1

############ HIDD
#
# To have Bluetooth mouse and keyboard support, get the
# Linux 2.6.6 patch or better from bluez.org, and set 
# HIDD_ENABLED to 1.
HIDD_ENABLED=1
HIDD_OPTIONS="--master --server"
# to make hidd always use a particular interface, use something
# like this, substituting the bdaddr of the interface:
# HIDD_OPTIONS="-i AA:BB:CC:DD:EE:FF --server"
#
# remove '--master' if you're having trouble working with Ericsson
# T630 phones with hidd operational at the same time.

# mogo mouse
HIDD_OPTIONS="--search --server"
HIDD_OPTIONS="-i hci0 --master -connect 00:02:76:01:99:94 --server"

############ COMPATIBILITY WITH OLD BLUEZ-PAN
# Compatibility: if old PAN config exists, use it
# rather than this file.
if test -f /etc/default/bluez-pan; then
    . /etc/default/bluez-pan
    return
fi
############

############ DUND
#
# Run dund -- this allows ppp logins. 1 for enabled, 0 for disabled.
DUND_ENABLED=0

# Arguments to dund: defaults to acting as a server
DUND_OPTIONS="--listen --persist"

# Run dund --help to see the full array of options.
# Here are some examples:
#
# Connect to any nearby host offering access
# DUND_OPTIONS="--search"
#
# Connect to host 00:11:22:33:44:55
# DUND_OPTIONS="--connect 00:11:22:33:44:55"
#
# Listen on channel 3
# DUND_OPTIONS="--listen --channel 3"

# Special consideration is needed for certain devices. Microsoft
# users see the --msdun option.  Ericsson P800 users will need to
# listen on channel 3 and also run 'sdptool add --channel=3 SP'

############ PAND
#
# Run pand -- ethernet: creates new network interfaces bnep<N>
# that can be configured in /etc/network/interfaces
# set to 1 for enabled, 0 for disabled
PAND_ENABLED=0

# Arguments to pand
# Read the PAN howto for ways to set this up
# http://bluez.sourceforge.net/contrib/HOWTO-PAN
PAND_OPTIONS=""

# example pand lines
#
# Act as the controller of an ad-hoc network
# PAND_OPTIONS="--listen --role GN"
#
# Act as a network access point: routes to other networks
# PAND_OPTIONS="--listen --role NAP"
#
# Act as a client of an ad-hoc controller with number 00:11:22:33:44:55
# PAND_OPTIONS="--role PANU --connect 00:11:22:33:44:55"
#
# Connect to any nearby network controller (access point or ad-hoc)
# PAND_OPTIONS="--role PANU --search"

############ SDPTOOL
# this variable controls the options passed to sdptool on boot, useful if you
# need to setup sdpd on boot.
# options are ;-separated, i.e. for every ; an sdptool instance will be
# launched
#
# examples:
# SDPTOOL_OPTIONS="add --channel=3 SP" # ericsson P800 serial profile
# SDPTOOL_OPTIONS="add --channel=8 OPUSH ; add --channel=9 FTRN" # motorola
#                                             # object push and file transfer
SDPTOOL_OPTIONS=""

```

Here is my /etc/init.d/bluetooth file:
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
#HCID_OPTIONS="-x -s"
HCID_OPTIONS=-x

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

```

here is my /etc/bluetooth/hcid.conf file:
```

#
# HCI daemon configuration file.
#

# HCId options
options {
        # Automatically initialize new devices
        autoinit yes;

        # Security Manager mode
        #   none - Security manager disabled
        #   auto - Use local PIN for incoming connections
        #   user - Always ask user for a PIN
        #
        security none;

        # Pairing mode
        #   none  - Pairing disabled
        #   multi - Allow pairing with already paired devices
        #   once  - Pair once and deny successive attempts
        pairing multi;

        # Default PIN code for incoming connections
        passkey "0000";
}

# Default settings for HCI devices
device {
        # Local device name
        #   %d - device id
        #   %h - host name
        name "%h-%d";

        # Local device class
        #class 0x3e0100;
        class 0x100100;

        # Default packet type
        #pkt_type DH1,DM1,HV1;

        # Inquiry and Page scan
        iscan enable; pscan enable;
        discovto 0;

        # Default link mode
        #   none   - no specific policy 
        #   accept - always accept incoming connections
        #   master - become master on incoming connections,
        #            deny role switch on outgoing connections
        lm accept;

        # Default link policy
        #   none    - no specific policy
        #   rswitch - allow role switch
        #   hold    - allow hold mode
        #   sniff   - allow sniff mode
        #   park    - allow park mode
        lp rswitch,hold,sniff,park;
}

# mogo mouse
device 00:02:76:01:99:94
{
        name "MoGo Mouse BT"
}

```

Any help is greatly appreciated.  Thanks!

---

### Post by anagor on 2007-08-19
maybe you should try restarting it in verbose mode, to see what service is failing exactly and then investigate the config of that service.

you can edit /etc/default/rcS file and change verbose to yes, and then restart the service.

---

### Post by abadfish on 2007-08-20
> **anagor said:**
> maybe you should try restarting it in verbose mode, to see what service is failing exactly and then investigate the config of that service.

you can edit /etc/default/rcS file and change verbose to yes, and then restart the service.

okay, I did that.  This is what happened:

```

 % sudo /etc/init.d/bluetooth restart
 * Restarting Bluetooth services                                                 * Stopping hidd...
Can't get device information: Host is down
 * Starting hidd...
 * Restarting rfcomm...
                                                                         [ OK ]
% 

```

any ideas??

---

### Post by abadfish on 2007-08-20
anybody????

---

### Post by abadfish on 2007-08-21
bump

---

### Post by liquid circuit on 2007-08-21
In /etc/default/bluetooth, try changing
```
HIDD_OPTIONS="--master --server"
```
to the following, replacing 99:99:99:99:99:99 with the MAC address of your bluetooth mouse...
```
HIDD_OPTIONS="--master --connect 99:99:99:99:99:99 --server"
```

You probably have already looked [here]("https://help.ubuntu.com/community/BluetoothMouse"), but check it just incase.  Apparently you need to run the sudo hidd --connect 99:99:99:99:99:99 command once before the mouse will automatically reconnect on reboot.

FYI:  I'm using a Logitech MX1000 (the bluetooth version that came with the MX5000 Bluetooth keyboard as a combo)... I have kinda been able to get it to reconnect on reboot; in order to do so I have to move it around during a critical portion of the boot process inorder for it to connect.  If I don't move it around, it must be in some sort of sleep state as it does not connect (X won't start, as my bluetooth mouse is the 'corepointer'; no other pointing device connected/available).  If you are running into a similar problem, try moving your mouse around constantly while booting.  If it DOES connect correctly under those conditions, you probably only really need to move it around for the portion of the reboot just before the X server states it couldn't start.  For those times that I forgot to move it around, I get to the terminal, log in, then run the following command:
```
sudo hidd --search
```
...then enter your password, and QUICKLY press the connect button on your mouse.  Sometimes it doesn't connect on the first time (probably just didn't press the button on the mouse at the right time).  If it connects successfully it should output something like:
```
Searching ...
        Connecting to device 99:99:99:99:99:99

```
At that point you'll want to restart X to get back into the GUI;  I do this by running the following command:
```
sudo /etc/init.d/gdm restart
```
FYI:  after running into these connection issues over and over, I decided to hurry up and make aliases/scripts to make this whole process easier to deal with (since I kept forgetting what the commands where :) ).  Once the aliases/scripts were in place, I wasn't so annoyed by the issue... but I still wish it was fixed.  Info on the web seems to indicate the reconnect on boot issue is a bug (can't remember exactly where it lies); hopefully it'll be fixed in Gutsy?

Bear in mind that I have probably wasted ~20 hours googling, trying to fix this reconnect issue, and I've yet to find a fix; this currently unresolvable issue may be specific to my mouse though (Logitech MX1000).

---

### Post by Jooky1138 on 2007-08-23
I've been having similar problems to you adafish

I'm running Fiesty with a Rocketfish Bluetooth keyboard and mouse and a SYBA usb bluetooth adapter.

I haven't been able to slove my problem, but here are some threads that looked promising but did not work for me

[https://help.ubuntu.com/community/BluetoothSetup](https://help.ubuntu.com/community/BluetoothSetup)
[http://ubuntuforums.org/showthread.php?t=227057](http://ubuntuforums.org/showthread.php?t=227057)

And after I get back from work I'm gonna try this one:

[http://ubuntuforums.org/showthread.php?p=1440347#post1440347](http://ubuntuforums.org/showthread.php?p=1440347#post1440347)

Good luck

-Jooker

---

### Post by Jooky1138 on 2007-08-23
Also let me know if you get a solution,  I need all the help I can't get

---

### Post by Jooky1138 on 2007-08-30
I found a workaround that is serving me.
I also upgraded to a iogear Bluetooth 2.0 usb adapter.  It supports the "park" feature, my syba adapter did not. I was having problems with disconnects when the keyboard and mouse went to sleep.

I did all the steps in this howto:
[https://help.ubuntu.com/community/BluetoothSetup](https://help.ubuntu.com/community/BluetoothSetup)

Then I added a few lines to /etc/rc.local:

```

sudo hciconfig hci0 up
sudo hciconfig hci0 reset
sudo hidd --connect <MAC_addr_mouse>
sudo hidd --connect <MAC_addr_keyboard>

```

Make sure it still ends with "exit 0"

The during startup use must have your devices in discovery mode, the should connect right before the login screen comes up.

It isn't perfect, but I no longer need a wired backup mouse/keyboard.

Also I find the hciconfig tools to be very useful

sudo hciconfig hciX <up/down/reset/features>

up turns on the device
down turns it off
reset -- you get the idea
features  handy if you want to know what options your adapter supports

Anyway if you are still having issues I hope this helps.

-Jooker

---

