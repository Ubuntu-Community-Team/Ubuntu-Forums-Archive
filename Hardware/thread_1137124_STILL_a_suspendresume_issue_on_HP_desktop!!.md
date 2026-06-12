---
title: "STILL a suspend/resume issue on HP desktop!!"
date: 2009-04-25
forum: Hardware
---

### Post by kakyoism on 2009-04-25
on my desktop machine (HP pavilion) with an nVidia 9500 card

The suspend cannot resume. I tried something that worked with my HP pavilion laptop two days ago, related to compiz. It doesn't help the desktop. Neither did a link on nVidia hardware help.
[http://blog.vaxius.net/?p=43]("http://blog.vaxius.net/?p=43")

Please help!

Here is related section of my /var/log/syslog:
Near the bottom are messages right after my hard-reboot....(ugh!)

"NetworkManager: <info>  Deactivating device eth0. " is the last record, although suspend did succeed. Just resume gives me only a flickering terminal cursor. I can switch to other consoles by ctrl-alt-F1, etc. But keyboard does not respond.


```
Apr 25 13:21:10 kakyo-home NetworkManager: <info>  Going to sleep. 
Apr 25 13:21:10 kakyo-home dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 6735
Apr 25 13:21:10 kakyo-home dhclient: killed old client process, removed PID file
Apr 25 13:21:10 kakyo-home avahi-daemon[6264]: Interface eth0.IPv4 no longer relevant for mDNS.
Apr 25 13:21:10 kakyo-home avahi-daemon[6264]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.1.104.
Apr 25 13:21:10 kakyo-home kernel: [  281.614705] bridge-eth0: disabling the bridge
Apr 25 13:21:10 kakyo-home kernel: [  281.672166] bridge-eth0: down
Apr 25 13:21:10 kakyo-home avahi-daemon[6264]: Withdrawing address record for fe80::21f:c6ff:feec:62fa on eth0.
Apr 25 13:21:10 kakyo-home avahi-daemon[6264]: Withdrawing address record for 192.168.1.104 on eth0.
Apr 25 13:21:10 kakyo-home kernel: [  281.760975] ACPI: PCI interrupt for device 0000:02:00.0 disabled
Apr 25 13:21:10 kakyo-home dhclient: Bind socket to interface: No such device
Apr 25 13:21:10 kakyo-home NetworkManager: <debug> [1240680070.992204] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/net_00_1f_c6_ec_62_fa'). 
Apr 25 13:21:10 kakyo-home NetworkManager: <info>  Deactivating device eth0. 
Apr 25 13:24:18 kakyo-home syslogd 1.5.0#1ubuntu1: restart.
Apr 25 13:24:18 kakyo-home kernel: Inspecting /boot/System.map-2.6.24-23-server
Apr 25 13:24:18 kakyo-home kernel: Loaded 28765 symbols from /boot/System.map-2.6.24-23-server.
```

---

### Post by yoasif on 2009-04-25
See [https://wiki.ubuntu.com/DebuggingKernelSuspendHibernateResume](https://wiki.ubuntu.com/DebuggingKernelSuspendHibernateResume) and [file bugs]("https://bugs.launchpad.net/ubuntu/+source/linux/+filebug/") as necessary.

---

