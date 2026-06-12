---
title: "Lucid cannot wakeup from suspend for Asus G51J-A1 Laptop"
date: 2010-08-28
forum: Hardware
---

### Post by kthakore on 2010-08-28
When the laptop suspends I cannot wake it up again. NOthing works. Keyboard, or mouse or even alt+sysreq stuff.


Here is my syslog after trying to suspend

```

Aug 28 15:54:55 kthakore-laptop NetworkManager: <info>  Sleeping...
Aug 28 15:54:55 kthakore-laptop NetworkManager: <info>  (wlan0): now unmanaged
Aug 28 15:54:55 kthakore-laptop NetworkManager: <info>  (wlan0): device state change: 3 -> 1 (reason 37)
Aug 28 15:54:55 kthakore-laptop NetworkManager: <info>  (wlan0): cleaning up...
Aug 28 15:54:55 kthakore-laptop NetworkManager: <info>  (wlan0): taking down device.
Aug 28 15:54:55 kthakore-laptop NetworkManager: <info>  (eth0): now unmanaged
Aug 28 15:54:55 kthakore-laptop NetworkManager: <info>  (eth0): device state change: 8 -> 1 (reason 37)
Aug 28 15:54:55 kthakore-laptop NetworkManager: <info>  (eth0): deactivating device (reason: 37).
Aug 28 15:54:55 kthakore-laptop NetworkManager: <info>  (eth0): canceled DHCP transaction, dhcp client pid 2155
Aug 28 15:54:55 kthakore-laptop NetworkManager: <WARN>  check_one_route(): (eth0) error -34 returned from rtnl_route_del(): Sucess#012
Aug 28 15:54:55 kthakore-laptop avahi-daemon[1123]: Withdrawing address record for 192.168.0.7 on eth0.
Aug 28 15:54:55 kthakore-laptop avahi-daemon[1123]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.0.7.
Aug 28 15:54:55 kthakore-laptop avahi-daemon[1123]: Interface eth0.IPv4 no longer relevant for mDNS.
Aug 28 15:54:55 kthakore-laptop NetworkManager: <info>  (eth0): cleaning up...
Aug 28 15:54:55 kthakore-laptop NetworkManager: <info>  (eth0): taking down device.
Aug 28 15:54:55 kthakore-laptop avahi-daemon[1123]: Withdrawing address record for fe80::4a5b:39ff:fe2e:48c5 on eth0.
Aug 28 15:54:55 kthakore-laptop NetworkManager: <info>  (eth0): carrier now OFF (device state 1)
Aug 28 15:54:59 kthakore-laptop AptDaemon: INFO: Quiting due to inactivity
Aug 28 15:54:59 kthakore-laptop AptDaemon: INFO: Shutdown was requested
Aug 28 15:56:33 kthakore-laptop kernel: imklog 4.2.0, log source = /proc/kmsg started.
Aug 28 15:56:33 kthakore-laptop rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="1142" x-info="http://www.rsyslog.com"] (re)start
Aug 28 15:56:33 kthakore-laptop rsyslogd: rsyslogd's groupid changed to 103
Aug 28 15:56:34 kthakore-laptop rsyslogd: rsyslogd's userid changed to 101
Aug 28 15:56:33 kthakore-laptop rsyslogd-2039: Could no open output file '/dev/xconsole' [try http://www.rsyslog.com/e/2039 ]
Aug 28 15:56:34 kthakore-laptop kernel: [    0.000000] Initializing cgroup subsys cpuset
Aug 28 15:56:34 kthakore-laptop kernel: [    0.000000] Initializing cgroup subsys cpu
Aug 28 15:56:34 kthakore-laptop kernel: [    0.000000] Linux version 2.6.32-24-generic (buildd@yellow) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #41-Ubuntu SMP Thu Aug 19 01:38:40 UTC 2010 (Ubuntu 2.6.32-24.41-generic 2.6.32.15+drm33.5)
Aug 28 15:56:34 kthakore-laptop kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-24-generic root=UUID=8972714a-c05f-4001-875d-c32ba861ab11 ro quiet splash

```

---

### Post by s3MA00RRNY on 2010-09-11
I am having a suspend problem with my G60Vx. The issues are probably related. My symptom is that the laptop gets stuck at the blinking cursor right before suspend. The problem seemed to come up after a recent update. I'll post a log as soon as I get one.

---

### Post by s3MA00RRNY on 2010-10-17
Don't know if you're still having the same problem, but mine left after a recent update. Let me know if you're having problems.

---

