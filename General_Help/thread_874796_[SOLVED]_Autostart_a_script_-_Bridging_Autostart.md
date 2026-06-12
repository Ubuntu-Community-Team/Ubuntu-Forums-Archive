---
title: "[SOLVED] Autostart a script - Bridging Autostart"
date: 2008-07-30
forum: General Help
---

### Post by PokerFacePenguin on 2008-07-30
I have a script (found online) for the purpose of starting bridging.  It has the following permissions:
> 
-rwxr-xr-x 1 root root 1126 2008-07-07 18:19 /etc/init.d/bridge.sh


The contents of the script are as follows:

> #!/bin/sh

# configure your static host info here and your user name

HOST_IP="192.168.x.x"  - edited to mask my details
HOST_NETMASK="255.255.255.0"
HOST_GATEWAY="192.168.x.x"  - edited to mask my details
HOST_IFACE="eth0"
USER_NAME=myusername   - edited to mask my details

case "$1" in
start)
echo -n "Setting up fancy dancy bridge networking"
ifconfig $HOST_IFACE 0.0.0.0 promisc up
brctl addbr umlbridge
brctl setfd umlbridge 0
brctl sethello umlbridge 0
brctl stp umlbridge off

ifconfig umlbridge $HOST_IP netmask $HOST_NETMASK up
route add default gw $HOST_GATEWAY
brctl addif umlbridge $HOST_IFACE

# first UML instance
tunctl -u $USER_NAME -t tap0
# added r/w privies
ifconfig tap0 0.0.0.0 promisc up
brctl addif umlbridge tap0
# second UML instance
# tunctl -u uml -t tap1
# ifconfig tap1 0.0.0.0 promisc up
# brctl addif umlbridge tap1
# and so on...
chmod 0666 /dev/net/tun
echo "."
;;
stop)
echo -n "Stopping networking bridge"
# add more tab1,tab2, etc as needed
ifconfig umlbridge down
brctl delif umlbridge $HOST_IFACE
brctl delif umlbridge tap0
brctl delbr umlbridge
tunctl -d tap0
ifconfig $HOST_IFACE $HOST_IP netmask $HOST_NETMASK up
route add default gw $HOST_GATEWAY
echo "."
;;
esac

exit 0 


This script will not run at boot but can be executed with sudo manually once I log in.  Any ideas on what am I doing wrong or how to get this to autostart at boot regardless of runlevel?

p.s.  I realize there are alot of posts on this subject.   I just have not found what I need.  Hoping there must be something unique about the reason it isn't working as I would like.  Thanks for any help in advance.

---

### Post by PokerFacePenguin on 2008-07-30
Ok, so I solved my own problem.  For the benefit of someone else having a similiar problem I needed to cd to the /etc/init.d directory and do a > update-rc.d scriptname defaults

---

