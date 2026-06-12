---
title: "82541GI constantly reconnects"
date: 2006-11-20
forum: Hardware &amp; Laptops
---

### Post by AlP on 2006-11-20
I am using an IBM X40 with Edgy. The Problem is, my ethernet connection constantly goes down and up again. 

[PHP]Nov 20 15:59:03 behemoth kernel: [17243224.220000] e1000: eth0: e1000_watchdog: NIC Link is Down
Nov 20 15:59:05 behemoth kernel: [17243225.940000] e1000: eth0: e1000_watchdog: NIC Link is Up 100 Mbps Full Duplex
Nov 20 15:59:39 behemoth kernel: [17243259.836000] e1000: eth0: e1000_watchdog: NIC Link is Down
Nov 20 15:59:40 behemoth kernel: [17243261.472000] e1000: eth0: e1000_watchdog: NIC Link is Up 100 Mbps Full Duplex
[/PHP]

I already disabled the network manager and switched from DHCP to static IPs ... but nothing helps.

It also does not seem to be a cable defect, for there are noch broken ethernet packages reported.

I could not finde anything useful in the web - may be my hardware is broken.

Greeting,
   AlP

---

### Post by srt4play on 2007-03-16
Hey, did you ever figure this out?  My work laptop is an X40. I had been running Dapper perfectly and like a moron I upgraded to Edgy and haven't been able to run my dhcp/tftp server setup for network booting registers. I notice these messages show up several times in /var/log/syslog:

 kernel: [ 3405.768000] e1000: eth0: e1000_watchdog: NIC Link is Up 10 Mbps Half Duplex

kernel: [ 3480.556000] e1000: eth0: e1000_watchdog: NIC Link is Down

Of course I reinstalled Dapper but it still doesn't work. ](*,) 

This is driving me crazy!

---

