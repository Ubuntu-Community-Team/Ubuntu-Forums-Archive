---
title: "[SOLVED] How to dump network usage"
date: 2008-10-08
forum: General Help
---

### Post by /////// on 2008-10-08
Whenever you click the network manager applet or go into the system monitor, you will be able to see the amount of received and sent network activity. How would I go about dumping this data every time I shut my computer down?

---

### Post by /////// on 2008-10-10
Bump

---

### Post by Calmatory on 2008-10-10
How do you want it to be dumped? Do you want to log the amount of transfered data or log the transfered data itself?

---

### Post by niteshifter on 2008-10-10
Hi,

The command "ifconfig" will give you that info:

```
ifconfig
```
Dumps info and stats on all network interfaces (eth0, eth1, etc.)

```
ifconfg eth0
```
Will give info and stats for just the eth0 interface. Output is like this:
```
eth0      Link encap:Ethernet  HWaddr 00:1C:23:FD:20:AE  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:23ff:fefd:20ae/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3278 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2409 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4315309 (4.1 MB)  TX bytes:371609 (362.8 KB)
          Interrupt:17 

```

```
ifconfig eth0 | grep bytes
```
will give you just what you asked for:
```
          RX bytes:4493656 (4.2 MB)  TX bytes:380445 (371.5 KB)
```

---

### Post by /////// on 2008-10-10
Lol yea niteshifter, thats what I wanted but is there anyway to get this to run during the shutdown process or just before shutdown?

---

### Post by /////// on 2008-10-10
Solved, I stumbled upon this thread: [http://ubuntuforums.org/showthread.php?t=436346](http://ubuntuforums.org/showthread.php?t=436346) and following it, I just added my code: "ifconfig ath0 | grep bytes >> /networklogging.log" inside the stop part of the script of /etc/init.d/gdm.
Hope this helps someone

---

