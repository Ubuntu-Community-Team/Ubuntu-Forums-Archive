---
title: "ddclient updating dyndns service with VPN gateway IP"
date: 2008-09-16
forum: General Help
---

### Post by zajc on 2008-09-16
I have a strange problem with ddclient and I don't know how to solve this :confused:

I have one NIC (eth0) and this is my ddclient configuration:

/etc/ddclient.conf

```
## ddclient configuration file
daemon=600                  # check every 600 seconds
syslog=yes                  # log update msgs to syslog
mail-failure=mail@gmail.com # Mail failed updates to user
pid=/var/run/ddclient.pid   # record PID in file.

## Detect IP with our CheckIP server
use=web, web=checkip.dyndns.com/, web-skip='IP Address'

## DynDNS username and password here
login=username
password=pass

## Default options
protocol=dyndns2
server=members.dyndns.org

## Dynamic DNS hosts
myname.dydns.com
```

I run ddclient as daemon.

/etc/default/ddclient

```
run_daemon=”true”
```

I am behind router. Everything is working OK, ddclient is udating dyndns service with my router IP, **until VPN connection (pptp) is started**. Then another ddclient session appeared and that process update my real IP to 172.16.3.x (my work VPN gateway). 

```
Sep 14 15:59:12 xxxx ddclient[6849]: SUCCESS:  updating myname.dyndns.com: good: IP address set to 172.16.3.9
Sep 14 16:05:12 xxxx ddclient[1423]: SUCCESS:  updating myname.dyndns.com: good: IP address set to 35.32.x.x
Sep 14 16:09:12 xxxx ddclient[6849]: SUCCESS:  updating myname.dyndns.com: good: IP address set to 172.16.3.9
Sep 14 16:15:12 xxxx ddclient[1423]: SUCCESS:  updating myname.dyndns.com: good: IP address set to 35.32.x.x
...
```

Now I have **two ddclient processes**, the first process is updating my dyndns address with router IP, and the second with 172.16.3.x. If I disconnect VPN session, the process remains. **The only workaround, at the moment, is to kill the 2nd process.** I realy don't know how to solve this :confused:

---

### Post by zajc on 2008-09-28
I find the solution. I need to change

/etc/default/ddclient

```
run_ipup="true"
```

to

```
run_ipup="false"
```

:)

---

### Post by elbeta on 2009-12-18
Thanks!!!
it works for me
:)

---

