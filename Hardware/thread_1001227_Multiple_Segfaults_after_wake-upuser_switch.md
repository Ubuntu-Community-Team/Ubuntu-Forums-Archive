---
title: "Multiple Segfaults after wake-up/user switch"
date: 2008-12-03
forum: Hardware
---

### Post by celafon on 2008-12-03
Hi,

I have a strange problem with my Acer TravelMate 3000, I have noticed this happens often after wake-up from suspend or a switch between local X users. I am not sure if this is software or hardware related.

When the 'thing' starts most of X apps are crashing whenever I try to do some action in them that probably involves some X-related feedback. Also there is no decoration, just windows. So when I recall a Gnome Terminal for instance and try to type anything - it crashes. Similar thing happens in other apps. Eventually the session crashes when trying to logout and the GDM is not able to bring itself back...

I have tried disabling composing, but the issue is still reproducible. Also when trying to re-launch an app, it seg faults straight away.

Here's the output of my syslog when this happened. The condition finished with kernel panic, but I did not know how to collect those logs so I just reset...

```
Dec  3 21:03:12 tytus kernel: [ 5293.608397] __ratelimit: 7 callbacks suppressed
Dec  3 21:03:12 tytus kernel: [ 5293.608405] gmplayer[11400]: segfault at 8b04ec87 ip b75ac3e2 sp bfdfd4a0 error 4 in libglib-2.0.so.0.1800.2[b7553000+b5000]
Dec  3 21:03:37 tytus kernel: [ 5317.842228] gmplayer[11478]: segfault at 0 ip b7668e67 sp bf8f5260 error 4 in libdbus-1.so.3.4.0[b7643000+36000]
Dec  3 21:03:42 tytus kernel: [ 5322.803223] gmplayer[11479]: segfault at 18 ip b757afa1 sp bf812130 error 4 in libdbus-1.so.3.4.0[b755e000+36000]
Dec  3 21:03:43 tytus kernel: [ 5323.874558] gtk-window-deco[5757]: segfault at e9d80805 ip 08054af9 sp bfe15d60 error 7 in gtk-window-decorator[8048000+13000]
Dec  3 21:04:01 tytus kernel: [ 5342.388998] gmplayer[11501]: segfault at b75f03f9 ip b75dfbb6 sp bfe53ef0 error 7 in libdbus-glib-1.so.2.1.0[b75d9000+1b000]
Dec  3 21:04:22 tytus kernel: [ 5363.526219] aptitude[11525]: segfault at c0e9f928 ip b7afeb56 sp bfff8768 error 7 in libc-2.8.90.so[b7a86000+158000]
Dec  3 21:04:41 tytus kernel: [ 5382.641817] gconftool-2[11539]: segfault at 8 ip b7c75073 sp bf9c7700 error 4 in libORBit-2.so.0.1.0[b7c57000+49000]
Dec  3 21:04:41 tytus gnome-session[5563]: WARNING: Running '/usr/bin/gconftool-2 --shutdown' at logout returned an exit status of '11' 
Dec  3 21:04:42 tytus NetworkManager: <info>  (eth1): device state change: 8 -> 3 
Dec  3 21:04:42 tytus NetworkManager: <info>  (eth1): deactivating device (reason: 38). 
Dec  3 21:04:42 tytus NetworkManager: <info>  eth1: canceled DHCP transaction, dhcp client pid 10313 
Dec  3 21:04:42 tytus NetworkManager: <WARN>  check_one_route(): (eth1) error -34 returned from rtnl_route_del(): Sucess  
Dec  3 21:04:42 tytus avahi-daemon[4546]: Withdrawing address record for 192.168.1.4 on eth1.
Dec  3 21:04:42 tytus avahi-daemon[4546]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.1.4.
Dec  3 21:04:42 tytus avahi-daemon[4546]: Interface eth1.IPv4 no longer relevant for mDNS.
Dec  3 21:04:42 tytus kernel: [ 5383.061094] nm-dispatcher.a[11563]: segfault at 18 ip b7febfa1 sp bf8a6330 error 4 in libdbus-1.so.3.4.0[b7fcf000+36000]
Dec  3 21:04:42 tytus bonobo-activation-server (bartek-11560): could not associate with desktop session: Failed to connect to socket /tmp/dbus-ViEzKruuRB: Connection refused
Dec  3 21:04:42 tytus kernel: [ 5383.074684] bonobo-activati[11564]: segfault at b7ed7ce0 ip b7eb7e77 sp b7856fc0 error 7 in libORBit-2.so.0.1.0[b7e8b000+49000]
Dec  3 21:04:44 tytus acpid: client connected from 11572[0:0] 
Dec  3 21:04:48 tytus kernel: [ 5389.416164] gdmgreeter[11587]: segfault at b8012f15 ip b7dc12f6 sp bffa9a10 error 7 in libgtk-x11-2.0.so.0.1400.4[b7ca6000+395000]
Dec  3 21:04:50 tytus acpid: client connected from 11598[0:0] 
Dec  3 21:04:54 tytus acpid: client connected from 11607[0:0] 
Dec  3 21:05:02 tytus acpid: client connected from 11631[0:0] 
Dec  3 21:05:08 tytus acpid: client connected from 11661[0:0] 
Dec  3 21:05:16 tytus ntpd[10429]: sendto(91.189.94.4) (fd=18): Invalid argument
Dec  3 21:05:17 tytus acpid: client connected from 11681[0:0] 
Dec  3 21:05:24 tytus NetworkManager: <info>  HAL disappeared 
Dec  3 21:05:25 tytus acpid: client connected from 11710[0:0] 

```

Any ideas?

---

