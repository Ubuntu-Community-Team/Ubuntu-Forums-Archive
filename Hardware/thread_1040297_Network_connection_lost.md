---
title: "Network connection lost"
date: 2009-01-15
forum: Hardware
---

### Post by Oenologist on 2009-01-15
Here it is.

I connect through the university network with the following config:

/etc/network/interfaces

```
#BEGIN

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
wpa-driver wired
wpa-conf /etc/wpa_supplicant/wpa_supplicant.conf

#END


```

/etc/wpa_supplicant/wpa_supplicant.conf

```
# BEGIN wired network configuration

ap_scan=0

ctrl_interface=/var/run/wpa_supplicant

network={
          key_mgmt=IEEE8021X
          eap=PEAP
          phase1="peaplabel=1"
          phase2="auth=MSCHAPV2"
          identity="xxxxxxx@aber.ac.uk"
          password="xxxxxxxxxxxx"
}

# ENG wired network configuration 

```

Moreover, there's a proxy setting of wwwcache.aber.ac.uk:8080

I work on Dell Inspiron 1525, Ubu 8.10. My girlfriend operates exactly on the same config (although on 8:04) and the connection works fine. 

But I suffer from notorious connection failure, and I have to reset the network every 15 minutes up to 1 hour with sudo /etc/init.d/networking restart

During the christmas time we were almost only people that used the university network, and the connection failures occured not frequent than every hour. I have seen nothing useful in system logs, but of course I'll supply you with them if needed. Now, when there are multiple users of the network, the interruptions occur even more frequently, each 15 minutes or so. It's getting more and more irritating so I ask for your assistance.

---

### Post by utnubuuser on 2009-01-15
I've seen at least 6 postings in the last 3 days regarding Dell laptop connection problems.  -- Same as what you're describing.  Try a search here for "Dell" within the last four or five days. >>Advanced Search

---

### Post by Oenologist on 2009-01-16
> **utnubuuser said:**
> I've seen at least 6 postings in the last 3 days regarding Dell laptop connection problems.  -- Same as what you're describing.  Try a search here for "Dell" within the last four or five days. >>Advanced Search

Nope. Most of them refer to wireless connection. I use wired. I browsed syslog and found that just before the crash a certain message appears:

```
Jan 16 10:50:01 dell-desktop /USR/SBIN/CRON[32730]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
```

Is it possible that some synchronization tool attempts to execute some process and disables the connection?

Here's the data concerning the networking restart:

```
jj@dell-desktop:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                           * Stopping the Firestarter firewall...
   ...done.
 * Starting the Firestarter firewall...
   ...done.
There is already a pid file /var/run/dhclient.eth0.pid with pid 1682
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/eth0/00:23:ae:03:d1:23
Sending on   LPF/eth0/00:23:ae:03:d1:23
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 144.124.103.254 port 67
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/eth0/00:23:ae:03:d1:23
Sending on   LPF/eth0/00:23:ae:03:d1:23
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPOFFER of 144.124.100.52 from 144.124.103.254
DHCPREQUEST of 144.124.100.52 on eth0 to 255.255.255.255 port 67
DHCPACK of 144.124.100.52 from 144.124.103.254
bound to 144.124.100.52 -- renewal in 75801 seconds.
 * Stopping the Firestarter firewall...
   ...done.
 * Starting the Firestarter firewall...
   ...done.
                              
```

Ifconfig:

```
jj@dell-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:23:ae:03:d1:23  
          inet addr:144.124.100.52  Bcast:144.124.103.255  Mask:255.255.248.0
          inet6 addr: fe80::223:aeff:fe03:d123/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:98430 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11861 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:23563041 (23.5 MB)  TX bytes:1909124 (1.9 MB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:188 errors:0 dropped:0 overruns:0 frame:0
          TX packets:188 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:24803 (24.8 KB)  TX bytes:24803 (24.8 KB)

```

---

