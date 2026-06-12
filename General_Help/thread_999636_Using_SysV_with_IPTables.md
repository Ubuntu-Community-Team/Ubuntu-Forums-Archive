---
title: "Using SysV with IPTables"
date: 2008-12-02
forum: General Help
---

### Post by saltera on 2008-12-02
I've written a small script which I had hoped I could use to start and stop iptables with the system.  

To this end I've tried to add the script to the sysv setup by copying it to /etc/init.d, setting as executable and registering it using sysv-rc-conf.  

If I run the script from the console everything seems ok eg:
  /etc/init.d/iptables start
  /etc/init.d/iptables stop

If I select levels 2345  in sysv-rc-conf then the system seems to get stuck starting and shutting down.

If I select levels 345 then iptables -L appears to be unchanged after starting and still gets stuck on shutdown.

```

#!/bin/bash

case "$1" in
    start)
        echo "Starting iptables"
       	/sbin/iptables -F INPUT
	/sbin/iptables -F FORWARD
	/sbin/iptables -F OUTPUT
       
	#default the policies to accept
        /sbin/iptables -P INPUT DROP
	/sbin/iptables -P FORWARD DROP
	/sbin/iptables -P OUTPUT DROP

	#established
	/sbin/iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT

	#outbound dns
	/sbin/iptables -A OUTPUT -p UDP --destination-port 53 -j ACCEPT

	#outbound http
	/sbin/iptables -A OUTPUT -p TCP --destination-port 80 -j ACCEPT

	#outbound https
	/sbin/iptables -A OUTPUT -p TCP --destination-port 443 -j ACCEPT

	#outbound irc - chat.freenode.net (ubuntu-uk)
	/sbin/iptables -A OUTPUT -p TCP --destination-port 8001 -j ACCEPT

	#outbound msn messenger
	/sbin/iptables -A OUTPUT -p TCP --destination-port 1863 -j ACCEPT	
	/sbin/iptables -A OUTPUT -p TCP --destination-port 7001 -j ACCEPT
	/sbin/iptables -A OUTPUT -p UDP --destination-port 7001 -j ACCEPT

	#output log everything else
	/sbin/iptables -A OUTPUT -j LOG

	
        ;;
    stop)
        echo "Shutting down iptables"
	#flush the existing chains
	/sbin/iptables -F INPUT
	/sbin/iptables -F FORWARD
	/sbin/iptables -F OUTPUT
       
	#default the policies to accept
        /sbin/iptables -P INPUT ACCEPT
	/sbin/iptables -P FORWARD ACCEPT
	/sbin/iptables -P OUTPUT ACCEPT
        ;;
    restart)
        $0 stop
        $0 start
        ;;
    status)
        iptables -L
        ;;
    *)
        echo "Usage: $0 {start|stop|restart|status}"
        exit 1
        ;;
esac

```

Any help getting to the bottom of this one would be greatly appreciated.

Kind regards
Saltera

---

