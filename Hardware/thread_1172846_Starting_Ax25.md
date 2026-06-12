---
title: "Starting Ax25"
date: 2009-05-29
forum: Hardware
---

### Post by FlaHAM on 2009-05-29
You've solved the riddle of installing the runtime ax25lib, ax25-apps and ax25-tools. You unraveled the mystery of attaching an ax25 device to a serial device and setting the operating parameters. Now how do you get the whole thing to work each time you boot up your computer? A bash script will do the trick, but where do you place it so that it starts up automatically?

Some Howto docs suggest placing in in rc.local, but it is really a system element. It should have it's own script in /etc/init.d/ You should be able to start, restart and stop the entire service from one script. OK that is easy enough, but how do we handle changes. You will want to add features to your packet services, experiment with settings and adapt to changing network configurations.
How about we start with a script in /etc/init.d/ that takes care of the basics – like start restart and stopping. It boils down to two operations Start & Stop. So we point Start to a specific file that takes care of details and Stop to another that halts the service in a organized manner. 
Start with the file in /etc/init.d and name it ax25. When we have our ax25 script placed in /etc/init.d/ we can setup the start links with the command :
[FONT="Arial"][B]update-rc.d ax25 defaults 95
[/B][/FONT]
An Example of a /etc/init.d/ax25 file

[FONT="Courier New"]#! /bin/bash
# Provided by Charles S Schuman ( K4GBB )
# 04/29/09
### BEGIN INIT INFO
# Provides: ax25
# Required-Start: /etc/ax25/ax25-up
# Required-Stop: /etc/ax25/ax25-down
# Default-Start: 3 4 5
# Default-Stop: 0 1 2 6
# Short-Description: Ax.25 initialization
# Description: This script provides the control for the ax.25 packet radio service.
#The fine tuning is accomplished via /etc/ax25/ax25-up and /etc/ax25/ax25-down.[/FONT]
[FONT="Courier New"]#
### END INIT INFO

# /etc/init.d/ax25
#
# Kernel-Parameter "ax25=yes|no" ?

      if [ "`grep -e [Aa][Xx]25=[Nn][Oo] /proc/cmdline`" != "" ] ; then
         echo -e "ax25: Aborting startup on user request (kernel boot parameter)."
         exit 1
      fi

case "$1" in
  start|-start)
    echo "/etc/init.d/ax25: Starting AX25..."
    /etc/ax25/ax25-up
  ;;

  stop|-stop)
    echo "Stopping AX25..."
    /etc/ax25/ax25-down
  ;;

  restart|-restart)
    echo "AX25 Restart"
    /etc/ax25/ax25-down
    sleep 1
    etc/ax25/ax25-up
  ;;

  status|-status)
    if [ ! -d /proc/sys/net/ax25 ] ; then
      echo "ax25 is down"
    else  
      echo "$(ls /proc/sys/net/ax25)" > /tmp/ax25-config.tmp
      read Select < /tmp/ax25-config.tmp
      i=0
      while [ "$Select" != "" ]
      do
      let i=i+1
      awk ' NR == '$i' { print $1 }' /tmp/ax25-config.tmp > /tmp/ax25-config-tmp
      read Select < /tmp/ax25-config-tmp
        if [ "$Select" != "" ]; then 
          /sbin/ifconfig "$Select"
        fi
      done
        if [ -z "$(uname -r | grep kjd)" ] ;then
          netstat --ax25
        else
          /sbin/ifconfig ipax0
          cat /proc/net/ax25
        fi  
    fi
   ;;

  *)
    echo "Usage: $0 {start|stop|restart|status}"
    exit 1
  ;;
esac

exit 0[/FONT]

Note that start points to /etc/ax25/ax25-up
Your ax25-up file might look like this:

[FONT="Courier New"]#!/bin/bash

# Set Sysctl values
sysctl -w kernel.panic=30
sysctl -w kernel.panic_on_oops=30

# Attach KISS-device /dev/ttyS0 to Port 0
 /usr/local/sbin/kissattach /dev/ttyS0 0 44.128.1.1 >/tmp/ax25-config.tmp
  awk '/device/ { print $7 }' /tmp/ax25-config.tmp > /tmp/ax25-config-tmp
  read Device < /tmp/ax25-config-tmp

# Install Parameter: Persistence=128, slot=10, TX-Delay=250
  /usr/local/sbin/kissparms -p 0 -r 228 -s 10 -l 20 -t 250

# Parms for Port0  (LAN) - Kernels > 2.6.17
cd /proc/sys/net/ax25/$Device/
echo 3100   > t1_timeout         	# (Frack) /100 = seconds ( 1 - 30) seconds
echo 1000   > t2_timeout         	# (RESPtime) /100 = .001 seconds (1 – 20)second
echo 300000 > t3_timeout         	# (Check) /600 = min (0 - 3600) seconds
echo 600000 > idle_timeout       	# Disconnect when idle /600 = min (0 or greater)
echo 0      > ax25_default_mode  	# AX25 Default Mode 0 = Normal, 1 = Extended (0)
echo 0      > ip_default_mode    	# IP Default Mode 0 = Standard (mod 7),1 = Extended (mod 127)(0)
echo 0      > backoff_type       	# Backoff 0 = Original, 1 = linear, 2 = exponential (1)
echo 256    > maximum_packet_length 	# Frame Size 1 - 512 (256)
echo 2 > connect_mode            	# Connect Mode 0 = None, 1 = Network, 2 = All (2)                        
echo 8 > maximum_retry_count     	# N2 (1 -31)
echo 180000 > dama_slave_timeout
echo 32 > extended_window_size
echo 2 > standard_window_size    	# Max frames
echo 0 > protocol

# Enable External Logons
  /usr/local/sbin/ax25d &
  echo $! > /var/run/ax25d.pid
  echo "ax25d started"

# Start Mheard daemon
 /usr/local/sbin/mheardd
  echo $! > /var/run/mheard.pid
  echo "mheardd Started"
# (End)
[/FONT]
Stop points to /etc/ax25/ax25-down:
It could look like this:

[FONT="Courier New"]#!/bin/bash

# Stop beacon if it is running
  if [ -e /var/run/beacon.pid ]; then
     killall beacon
     rm -f /var/run/beacon.pid
     echo Beacon stopped
  fi

# Stop netromd if it is running
  if [ -e /var/run/netromd.pid ]; then
     killall netromd
     rm -f /var/run/netromd.pid
     echo Netrom Stopped
  fi

# Stop mheardd if it is running
  if [ -e /var/run/mheard.pid ]; then
    killall mheardd
    rm -f /var/run/mheard.pid
    echo Mheardd Stopped
  fi

# Stop ax25d if it is running
  if [ -e /var/run/ax25d.pid ]; then
    killall ax25d
    rm -f /var/run/ax25d.pid
    echo AX25d Stopped
  fi

# Stop ax25ipd if it is running
  if [ -e /var/run/ax25ipd.pid ]; then
    killall ax25ipd
    rm -f /var/run/ax25ipd.pid
    echo AX25ipd Stopped
  fi

# Stop ax25rtd if it is running
  if [ -e /var/run/ax25rtd.pid ]; then
    killall ax25rtd
    rm -f /var/run/ax25rtd.pid
    echo "AX25rtd Stopped"
   fi
# Stop Monitor program
  if [ -e /var/run/listen.pid ]; then
    killall listen
    rm -f /var/run/listen.pid
    echo "Stop Monitor"
  fi
# Detach Ax/Sp Devices
  echo "$(ls /proc/sys/net/ax25)" > /tmp/ax25-config.tmp
# awk '/rose/{print $1}' /etc/ax25/rsports >> /tmp/ax25-config.tmp
  read Select < /tmp/ax25-config.tmp
  i=0
  while [ "$Select" != "" ]
  do
   let i=i+1
   awk ' NR == '$i' { print $1 }' /tmp/ax25-config.tmp > /tmp/ax25-config-tmp
   read Select < /tmp/ax25-config-tmp
   if [ "$Select" != "" ]; then 
    ifconfig "$Select" down
    echo " $Select Stopped" 
  fi
  done

# Stop Kissattach
  killall -KILL kissattach > /dev/null

  echo "Ax25 Stopped"
# End of ax25-down[/FONT]

---

