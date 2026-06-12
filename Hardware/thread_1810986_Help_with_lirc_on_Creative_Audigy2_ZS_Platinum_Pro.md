---
title: "Help with lirc on Creative Audigy2 ZS Platinum Pro (half working)."
date: 2011-07-24
forum: Hardware
---

### Post by Menthu_Rae on 2011-07-24
EDIT: OH MY GOD I FIXED IT! Turns out I had copy > pasted some code from online and as such had ” quotation marks in the config rather than "....!!!!! ARRRRGHHH! So glad it was so simple though and that I wasn't going insane (the config was right sans those quote marks!). Haha SWEET~

[COLOR="Silver"]Hi there,

I am trying to get lirc working correctly with my Creative Audigy2 ZS Platinum Pro.

I have it working **but** I have use a custom script in /etc/init.d/ to launch it on bootup and additionally I have to to run some commands from terminal after suspend/resume.

I can **only** get lirc to work if I run what I have put in **lirc.custom** as opposed to the standard **lirc** script.

Can someone please help me to get it to work using the standard lirc "service" in /etc/init.d/ ? For the life of me, I cannot see what the problem is! :confused:

OK, so... this is what I have to do to get lirc to work properly/as I require:

[INDENT]**/etc/init.d/lirc.custom**
```

echo -en "\xf0\x00\x20\x21\x61\x00\x00\x00\x7f\x00\xf7" > /dev/snd/midiC0D1
sudo /usr/sbin/lircd -H livedrive_midi -d /dev/snd/midiC0D1

```[/INDENT]

If I do this... **everything works FINE** - _[SIZE="3"]but[/SIZE]_ it is not ideal since I can't tie it in with suspend/resume scripts!

This is what happens if I try to use the lirc "service"...

[INDENT]```
sudo service lirc start
/etc/lirc/hardware.conf: 4: LiveDrive: not found
 * Loading LIRC modules                                                  [ OK ] 
 * Unable to load LIRC kernel modules. Verify your
 * selected kernel modules in /etc/lirc/hardware.conf

```[/INDENT]

Here is my **/etc/lirc/hardware.conf** (note- I had ” quotation marks instead of " which resulted in the problem above.)

[INDENT]```
# /etc/lirc/hardware.conf
 #
 #Chosen Remote Control
 REMOTE="Creative LiveDrive midi"
 REMOTE_MODULES=""
 REMOTE_DRIVER="livedrive_midi"
 REMOTE_DEVICE="/dev/snd/midiC0D1"
 REMOTE_LIRCD_CONF="creative/lircd.conf.livedrive"
 REMOTE_LIRCD_ARGS="-d /dev/snd/midiC0D1 -H livedrive_midi"

 #Chosen IR Transmitter
 TRANSMITTER="None"
 TRANSMITTER_MODULES=""
 TRANSMITTER_DRIVER=""
 TRANSMITTER_DEVICE=""
 TRANSMITTER_LIRCD_CONF=""
 TRANSMITTER_LIRCD_ARGS=""

 #Enable lircd
 START_LIRCD="true"

 #Don't start lircmd even if there seems to be a good config file
 #START_LIRCMD="false"

 #Try to load appropriate kernel modules
 LOAD_MODULES="true"

 # Default configuration files for your hardware if any
 LIRCMD_CONF=""

 #Forcing noninteractive reconfiguration
 #If lirc is to be reconfigured by an external application
 #that doesn't have a debconf frontend available, the noninteractive
 #frontend can be invoked and set to parse REMOTE and TRANSMITTER
 #It will then populate all other variables without any user input
 #If you would like to configure lirc via standard methods, be sure
 #to leave this set to "false"
 FORCE_NONINTERACTIVE_RECONFIGURATION="false"
 START_LIRCMD=""
REMOTE_SOCKET=""
TRANSMITTER_SOCKET=""
```[/INDENT]

Here is the standard lirc service, i.e. /etc/init.d/lirc...

[INDENT]```
#! /bin/sh
### BEGIN INIT INFO
# Provides:          lirc
# Required-Start:    $remote_fs $syslog
# Required-Stop:     $remote_fs $syslog
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: Starts LIRC daemon.
# Description:       LIRC is used to control different
#                    infrared receivers and transceivers.
### END INIT INFO

load_modules ()
{
	MODULES_MISSING=false

	log_daemon_msg "Loading LIRC modules"
	for mod in $*; do
		if [ $mod = "udev" ]; then
			log_end_msg 0
			log_success_msg "Restarted via udev, don't reload modules"
			break
		else
			modprobe $mod 2> /dev/null || MODULES_MISSING=true
		fi
	done
	log_end_msg $?

	if $MODULES_MISSING; then
		log_failure_msg "Unable to load LIRC kernel modules. Verify your"
		log_failure_msg "selected kernel modules in /etc/lirc/hardware.conf"
		START_LIRCMD=false
		START_LIRCD=false
	fi
}

build_remote_args ()
{
	REMOTE_ARGS="$*"

	#For remote only detection support, we need
	#both REMOTE_DEVICE and TRANSMITTER_DEVICE undefined
	if [ -z "$REMOTE_DEVICE" ] && [ -z "$TRANSMITTER_DEVICE" ] && [ -c $dev ]; then
		REMOTE_DEVICE="$dev"
	fi

	#If we have a REMOTE_DEVICE or REMOTE_DRIVER defined (either because no devices
	#were defined, OR if we explicitly did), then populate REMOTE_ARGS
	if [ ! -z "$REMOTE_DEVICE" ] || [ ! -z "$REMOTE_DRIVER" ]; then
		if [ -n "$REMOTE_DEVICE" ] && [ "$REMOTE_DEVICE" != "none" ]; then
			REMOTE_ARGS="--device=$REMOTE_DEVICE $REMOTE_ARGS"
		fi
		if [ -n "$REMOTE_DRIVER" ] && [ "$REMOTE_DRIVER" != "none" ]; then
			REMOTE_ARGS="--driver=$REMOTE_DRIVER $REMOTE_ARGS"
		fi

		#Now, if we ALSO have a transmitter defined, add some args
		#To make the first lircd listen up
		if [ ! -z "$TRANSMITTER_DEVICE" ] || [ ! -z "$TRANSMITTER_DRIVER" ]; then
			REMOTE_ARGS="$REMOTE_ARGS --listen"
		fi
		REMOTE_ARGS="--output=$REMOTE_SOCKET $REMOTE_ARGS"
	fi
	echo $REMOTE_ARGS
}

build_transmitter_args ()
{
	TRANSMITTER_ARGS="$*"

	#Transmitters must be explicitly be defined
	if [ ! -z "$TRANSMITTER_DEVICE" ] || [ ! -z "$TRANSMITTER_DRIVER" ]; then
		if [ -n "$TRANSMITTER_DEVICE" ] && [ "$TRANSMITTER_DEVICE" != "none" ]; then
			TRANSMITTER_ARGS="--device=$TRANSMITTER_DEVICE $TRANSMITTER_ARGS"
		fi
		if [ -n "$TRANSMITTER_DRIVER" ] && [ "$TRANSMITTER_DRIVER" != "none" ]; then
			TRANSMITTER_ARGS="--driver=$TRANSMITTER_DRIVER $TRANSMITTER_ARGS"
		fi

		#Now, if we ALSO have a remote defined, add some args
		#To make the second lircd connect
		if [ ! -z "$REMOTE_DEVICE" ] || [ ! -z "$REMOTE_DRIVER" ]; then
			TRANSMITTER_ARGS="$TRANSMITTER_ARGS --connect=localhost:8765 --pidfile=/var/run/lirc/lircd1.pid"
		fi
		TRANSMITTER_ARGS="--output=$TRANSMITTER_SOCKET $TRANSMITTER_ARGS"
	fi
	echo $TRANSMITTER_ARGS
}

. /lib/lsb/init-functions

test -f /usr/sbin/lircd || exit 0
test -f /usr/sbin/lircmd || exit 0

START_LIRCMD=true
START_LIRCD=true
START_IREXEC=true

echo -en "\xf0\x00\x20\x21\x61\x00\x00\x00\x7f\x00\xf7" > /dev/snd/midiC0D1

mkdir -p /var/run/lirc

if [ -f /etc/lirc/hardware.conf ];then
	. /etc/lirc/hardware.conf
fi

if [ ! -f /etc/lirc/lircd.conf ] || grep -q "^#UNCONFIGURED" /etc/lirc/lircd.conf; then
	if [ "$1" = "start" ]; then
		log_success_msg "No valid /etc/lirc/lircd.conf has been found."
		log_success_msg "Remote control support has been disabled."
		log_success_msg "Reconfigure LIRC or manually replace /etc/lirc/lircd.conf to enable."
	fi

	START_LIRCD=false
	START_LIRCMD=false
	START_IREXEC=false
fi

if [ ! -f /etc/lirc/lircmd.conf ] || grep -q "^#UNCONFIGURED" /etc/lirc/lircmd.conf; then
	START_LIRCMD=false
fi

if [ ! -f /etc/lirc/lircrc ] || grep -q "^#UNCONFIGURED" /etc/lirc/lircrc; then
	START_IREXEC=false
fi

#We need default socket locations
OLD_SOCKET="/dev/lircd"
if [ -z "$REMOTE_SOCKET" ]; then
	REMOTE_SOCKET="/var/run/lirc/lircd"
fi
if [ -z "$TRANSMITTER_SOCKET" ]; then
	TRANSMITTER_SOCKET="/var/run/lirc/lircd"
	#Now, if we ALSO have a remote defined,
	#change the default transmitter socket
	if [ ! -z "$REMOTE_DEVICE" ] || [ ! -z "$REMOTE_DRIVER" ]; then
		TRANSMITTER_SOCKET="${TRANSMITTER_SOCKET}1"
	fi
fi

case "$1" in
	start)
		if [ "$LOAD_MODULES" = "true" ] && [ "$START_LIRCD" = "true" ]; then
			load_modules $2 $REMOTE_MODULES $TRANSMITTER_MODULES $MODULES
		fi

		if [ "$START_LIRCD" = "true" ]; then
			[ -d "/var/run/lirc" ] || mkdir -p "/var/run/lirc"
			log_daemon_msg "Starting remote control daemon(s) : LIRC "
			REMOTE_LIRCD_ARGS=`build_remote_args $REMOTE_LIRCD_ARGS`
			TRANSMITTER_LIRCD_ARGS=`build_transmitter_args $TRANSMITTER_LIRCD_ARGS`

			#if we have a remote defined, it is primary process
			if [ ! -z "$REMOTE_LIRCD_ARGS" ]; then
				start-stop-daemon --start --quiet --oknodo --exec /usr/sbin/lircd -- $REMOTE_LIRCD_ARGS < /dev/null
				log_end_msg $?
				if [ -S "$REMOTE_SOCKET" -a "$OLD_SOCKET" != "$REMOTE_SOCKET" ]; then
					rm -f $OLD_SOCKET && ln -s $REMOTE_SOCKET $OLD_SOCKET
				fi 

				#now if we additionally have a transmitter defined, it is secondary process
				if [ ! -z "$TRANSMITTER_LIRCD_ARGS" ]; then
					/usr/sbin/lircd $TRANSMITTER_LIRCD_ARGS < /dev/null
					if [ -S "$TRANSMITTER_SOCKET" ]; then
						rm -f ${OLD_SOCKET}1 && ln -s $TRANSMITTER_SOCKET ${OLD_SOCKET}1
					fi 
				fi
			elif [ ! -z "$TRANSMITTER_LIRCD_ARGS" ]; then
				start-stop-daemon --start --quiet --oknodo --exec /usr/sbin/lircd -- $TRANSMITTER_LIRCD_ARGS < /dev/null
				log_end_msg $?
				if [ -S "$TRANSMITTER_SOCKET" -a "$OLD_SOCKET" != "$TRANSMITTER_SOCKET" ]; then
					rm -f $OLD_SOCKET && ln -s $TRANSMITTER_SOCKET $OLD_SOCKET
				fi 
			else
				log_end_msg 1
			fi
		fi

		if [ "$START_LIRCMD" = "true" ]; then
			[ -d "/var/run/lirc" ] || mkdir -p "/var/run/lirc"
			log_daemon_msg "Starting remote control mouse daemon : LIRCMD "
			start-stop-daemon --start --quiet --oknodo --exec /usr/sbin/lircmd < /dev/null
			log_end_msg $?
		fi

		if [ "$START_IREXEC" = "true" ]; then
			[ -d "/var/run/lirc" ] || mkdir -p "/var/run/lirc"
			log_daemon_msg "Starting execution daemon: irexec"
			start-stop-daemon --start --quiet --oknodo --exec /usr/bin/irexec -- -d /etc/lirc/lircrc < /dev/null
			log_end_msg $?
		fi
		;;
	stop)
		if [ "$START_IREXEC" = "true" ]; then
			log_daemon_msg "Stopping execution daemon: irexec"
			start-stop-daemon --stop --quiet --exec /usr/bin/irexec
			log_end_msg $?
		fi

		if [ "$START_LIRCMD" = "true" ]; then
			log_daemon_msg "Stopping remote control mouse daemon: LIRCMD"
			start-stop-daemon --stop --quiet --exec /usr/sbin/lircmd
			log_end_msg $?
		fi

		if [ "$START_LIRCD" = "true" ]; then
			log_daemon_msg "Stopping remote control daemon(s): LIRC"
			start-stop-daemon --stop --quiet --exec /usr/sbin/lircd
			log_end_msg $?
			[ -h "$OLD_SOCKET" ] && rm -f $OLD_SOCKET
			[ -h "${OLD_SOCKET}1" ] && rm -f ${OLD_SOCKET}1
		fi
		;;
	reload|force-reload)
		if [ "$START_IREXEC" = "true" ]; then
			start-stop-daemon --stop --quiet --signal 1 --exec /usr/bin/irexec
		fi

		if [ "$START_LIRCD" = "true" ]; then
			start-stop-daemon --stop --quiet --signal 1 --exec /usr/sbin/lircd
		fi

		if [ "$START_LIRCMD" = "true" ]; then
			start-stop-daemon --stop --quiet --signal 1 --exec /usr/sbin/lircmd
		fi
		;;
	restart)
		$0 stop
		#passes parameter $2 which is possibly our udev paramater
		$0 start $2
		;;
	*)
		echo "Usage: /etc/init.d/lircd {start|stop|reload|restart|force-reload}"
	exit 1
esac

exit 0
```[/INDENT]

Here are the file permissions for /snd/dev/midiC0D1...

[INDENT]```
ls -ltra | grep midiC0D1

crw-rw----+  1 root audio 116,  5 2011-07-24 11:14 midiC0D1

```[/INDENT]

Here is a cat of /snd/dev/midiC0D1 **without** lirc running (so, the remote is working fine and being received)...

[INDENT]```
cat /dev/snd/midiC0D1 

&#65533; !`
AD^!&#65533;&#65533; !`
AD1N&#65533;&#65533; !`
ADa&#65533;&#65533; !`
AD.Q

```[/INDENT]

Similarly, here is a sample output of irw showing that everything is working when I run **lirc.custom** (so lirc is interpreting everything fine)...

[INDENT]```
irw

0000000083227b84 00 up rm1000w
0000000083228d72 00 down rm1000w
0000000083228778 00 left rm1000w
000000008322758a 00 right rm1000w

```[/INDENT]

[/COLOR]

---

