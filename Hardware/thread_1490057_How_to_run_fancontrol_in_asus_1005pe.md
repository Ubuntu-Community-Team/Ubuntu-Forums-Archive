---
title: "How to run fancontrol in asus 1005pe?"
date: 2010-05-21
forum: Hardware
---

### Post by vickoxy on 2010-05-21
Hi,
i want to have fancontrol running in one asus 1005pe. I have lm-sensors installed, tried to follow this instructions:

[http://ubuntuforums.org/showthread.php?t=2780](http://ubuntuforums.org/showthread.php?t=2780)

but i can not find lm-sensors source. So i get this error message:
```
# pwmconfig revision 5770 (2009-09-16)
This program will search your sensors for pulse width modulation (pwm)
controls, and test each one to see if it controls a fan on
your motherboard. Note that many motherboards do not have pwm
circuitry installed, even if your sensor chip supports pwm.

We will attempt to briefly stop each fan using the pwm controls.
The program will attempt to restore each fan to full speed
after testing. However, it is ** very important ** that you
physically verify that the fans have been to full speed
after the program has completed.

/usr/sbin/pwmconfig: There are no pwm-capable sensor modules installed

```

sensors are showing no fan:

```
# pwmconfig revision 5770 (2009-09-16)
This program will search your sensors for pulse width modulation (pwm)
controls, and test each one to see if it controls a fan on
your motherboard. Note that many motherboards do not have pwm
circuitry installed, even if your sensor chip supports pwm.

We will attempt to briefly stop each fan using the pwm controls.
The program will attempt to restore each fan to full speed
after testing. However, it is ** very important ** that you
physically verify that the fans have been to full speed
after the program has completed.

/usr/sbin/pwmconfig: There are no pwm-capable sensor modules installed

```

So, anyone any idea?

---

### Post by 2hot6ft2 on 2010-05-21
Perhaps a search of synaptic for "asus fan control" which would find digitools.
```
A set of tools to control ASUS Digimatrix embedded hardware

This package is a combination of the previous programs asusfan and setpanel.
Included in this package are the following tools:
[B]  digifan:   allows fan speed control
             (formerly asusfan)
[/B]
  digipanel: allows control of the LED display, and volume knob controls
             the soundcard master mixer channel
             (formerly part of setpanel)

  digiradio: allows control of the in-built radio
             (formerly part of setpanel)

  digiwake:  allows for Wake-On-CIR (wake on remote) with existing
             versions of LIRC that support the digimatrix. This program
             just needs to be run after lircd, and the digimatrix will
             power on when pressing the music/(on/off) button on the
             remote control.
```
:guitar:

---

### Post by vickoxy on 2010-05-21
> **2hot6ft2 said:**
> Perhaps a search of synaptic for "asus fan control" which would find digitools.
```
A set of tools to control ASUS Digimatrix embedded hardware

This package is a combination of the previous programs asusfan and setpanel.
Included in this package are the following tools:
[B]  digifan:   allows fan speed control
             (formerly asusfan)
[/B]
  digipanel: allows control of the LED display, and volume knob controls
             the soundcard master mixer channel
             (formerly part of setpanel)

  digiradio: allows control of the in-built radio
             (formerly part of setpanel)

  digiwake:  allows for Wake-On-CIR (wake on remote) with existing
             versions of LIRC that support the digimatrix. This program
             just needs to be run after lircd, and the digimatrix will
             power on when pressing the music/(on/off) button on the
             remote control.
```
:guitar:

Thanks, but i can not find it. Is it in normal ubuntu packages or should i add some new repositories?

---

### Post by vickoxy on 2010-05-22
It seems that there are few or no fan control apps that are working in lucid? Or i am wrong?

I thought that fancontrol is tool that should work on every computer, but in lucid -as i read - it doesn´t work...

---

### Post by vickoxy on 2010-05-22
bump

---

### Post by vickoxy on 2010-05-22
bump

---

### Post by MilitantPotato on 2010-06-07
Replying here as well as to the PM you sent.

I installed: fancontrol libsensors4 lm-sensors sensord 

I had to reboot to get the sensors-detect to work correctly. 

I ran sensors-detect, rebooted, then ran pwmconfig to make a fancontrol configuration file (tell it to save to /etc/fancontrol when it asks.)
Then I was good to go.

You can set temps as you choose, my setup seems to work well, the fan is nearly inaudible when idling, and keeps the core temps bellow 58C most of the time.

Here's my /etc/init.d/fancontrol
```
#! /bin/sh

### BEGIN INIT INFO
# Provides:          fancontrol
# Required-Start:    $remote_fs
# Required-Stop:     $remote_fs
# Default-Start:     2 3 4 5
# Default-Stop:
# Short-Description: fancontrol
# Description:       fan speed regulator
### END INIT INFO

. /lib/lsb/init-functions

[ -f /etc/default/rcS ] && . /etc/default/rcS
PATH=/bin:/usr/bin:/sbin:/usr/sbin
DAEMON=/usr/sbin/fancontrol
DESC="fan speed regulator"
NAME="fancontrol"
PIDFILE=/var/run/fancontrol.pid
CONF=/etc/fancontrol

test -x $DAEMON || exit 0

case "$1" in
  start)
  	if [ -f $CONF ] && [ -n "`grep INTERVAL $CONF | cut -d= -f2`" ]; then
		if [ -n "`grep DEVPATH $CONF | cut -d= -f2`" ] && [ -n "`grep DEVNAME $CONF | cut -d= -f2`" ] ; then
			log_daemon_msg "Starting $DESC" "$NAME"
			start-stop-daemon --start --quiet --background --pidfile $PIDFILE --startas $DAEMON
			log_end_msg $?
		else
			log_failure_msg "Not starting fancontrol, outdated configuration file; please re-run pwmconfig."
		fi
	else
		if [ "$VERBOSE" != no ]; then
			log_warning_msg "Not starting fancontrol; run pwmconfig first."
		fi
	fi
	;;
  stop)
	log_daemon_msg "Stopping $DESC" "$NAME"
	start-stop-daemon --stop --quiet --pidfile $PIDFILE --oknodo --startas $DAEMON
	rm -f $PIDFILE
	log_end_msg $?
	;;
  restart)
  	$0 stop
	sleep 3
	$0 start
	;;
  force-reload)
	if start-stop-daemon --stop --test --quiet --pidfile $PIDFILE --startas $DAEMON ; then
		$0 restart
	fi
	;;
  status)
	status_of_proc $DAEMON $NAME && exit 0 || exit $?
	;;
  *)
	log_success_msg "Usage: /etc/init.d/fancontrol {start|stop|restart|force-reload|status}"
	exit 1
	;;
esac

exit 0

```
If you need to create that file, make sure to set it executable. You shouldn't need to create it, but stranger things have happened.

here's my /etc/fancontrol that was created by pwmconfig after a little tweaking.
```
# Configuration file generated by pwmconfig, changes will be lost
INTERVAL=2
DEVPATH=hwmon1=devices/platform/eeepc hwmon2=devices/platform/coretemp.0
DEVNAME=hwmon1=eeepc hwmon2=coretemp
FCTEMPS= hwmon1/pwm1=hwmon2/device/temp1_input
FCFANS= hwmon1/pwm1=
MINTEMP= hwmon1/pwm1=45
MAXTEMP= hwmon1/pwm1=55
MINSTART= hwmon1/pwm1=80
MINSTOP= hwmon1/pwm1=0
MAXPWM= hwmon1/pwm1=255
```

Also, here's the output of 'sensors' if you need to compare.

```
sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +62.0°C  (crit = +98.0°C)                  

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +49.0°C  (crit = +100.0°C)                  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +49.0°C  (crit = +100.0°C)                  

eeepc-isa-0000
Adapter: ISA adapter
fan1:       3983 RPM
```

---

### Post by vickoxy on 2010-06-07
Thanks

---

