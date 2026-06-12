---
title: "Sony VAIO Z1SP &amp; Wireless switch"
date: 2005-03-19
forum: Hardware &amp; Laptops
---

### Post by Brathahn on 2005-03-19
Was looking for a solution to bring the wireless network up when I use the Wireless Switch on the Z1. Couldn't find anything so I decided to do it myself... Here's the result after 20 mins:

- prerequisite is the IPW2100 already loaded.

This goes into /etc/init.d:

[B]#!/bin/sh
# rf_switch -- ifup / ifdown eth1 according to rf_kill state
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
DAEMON=/home/brathahn/bin/rf_switch.sh
NAME=rf_switch
DESC="RF Switch Watchdog"

set -e

case "$1" in
  start)
    echo -n "Starting $DESC: $NAME"
    start-stop-daemon --start --quiet --pidfile /var/run/$NAME.pid \
    --exec $DAEMON &
    echo "."
    ;;
  stop)
    echo -n "Stopping $DESC: $NAME"
    echo "."
    ;;
  restart)
    $0 stop
    sleep 1
    $0 start
    ;;
  *)
    echo "Usage: /etc/init.d/rf_switch {start|stop|restart}"
    exit 1
esac

[/B]
And this is the rf_switch.sh in the ~/bin directory:

[B]#!/bin/sh
# rf_switch.sh -- ifup / ifdown eth1 according to rf_kill state

while true; do
  if cat /sys/bus/pci/drivers/ipw2100/*/rf_kill | grep -q -i "2" ; then
    # RF Switch is OFF
    if [ "`grep eth1 /etc/network/ifstate`" == "eth1=eth1" ]; then
      # eth1 is UP and RF Switch is OFF -->  shutdown eth1
      ifdown eth1 > /dev/null
    else
      # eth1 is DOWN and RF Switch is OFF --> do nothing
      echo > /dev/null
    fi
  fi

  if cat /sys/bus/pci/drivers/ipw2100/*/rf_kill | grep -q -i "0" ; then
    # RF Switch is ON
    if [ "`grep eth1 /etc/network/ifstate`" == "eth1=eth1" ]; then
      # eth1 is UP and RF Switch is ON --> do nothing
      echo > /dev/null
    else
      # eth1 is DOWN and RF Switch is ON --> startup eth1
      ifup eth1  > /dev/null
    fi
  fi  
  sleep 3
done
[/B]

Works fine but it's not very elegant... specially the echo > /dev/null & ifup / ifdown > /dev/null stuff. Also there's slight cosmetic problem. Since it gets started as a daemon during bootup on vc1 I get some output from the ifup / ifdown commands on vc1 which looks a bit weird since nobody is logged on there.

Maybe someone with more experience in scripting can polish it up....

---

