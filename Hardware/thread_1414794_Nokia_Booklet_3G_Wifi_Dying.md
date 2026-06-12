---
title: "Nokia Booklet 3G Wifi Dying"
date: 2010-02-24
forum: Hardware
---

### Post by thursdasy on 2010-02-24
Hey everyone, every 30 minutes or so I loose my connection for no apparent reason. It seems there is a driver issue, I installed:
```
linux-backports-modules-2.6.31-19-generic
``` 

as I read this might help but it didn't seem to do much.

Here is what happens when I "loose" connection. Please note it doesn't actually appear discounted in NetworkManager. 

There are two examples of what appears in syslog when I loose connection.

```

thursdasy@booklet-phyn3t:~$ tail /var/log/syslog
Feb 23 21:51:37 booklet-phyn3t NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake
Feb 23 21:51:37 booklet-phyn3t NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> completed
Feb 23 21:51:47 booklet-phyn3t pulseaudio[1594]: ratelimit.c: 3 events suppressed
Feb 23 21:51:49 booklet-phyn3t wpa_supplicant[944]: WPA: Group rekeying completed with 00:19:e3:fa:28:8a [GTK=TKIP]
Feb 23 21:51:49 booklet-phyn3t NetworkManager: <info>  (wlan0): supplicant connection state:  completed -> group handshake
Feb 23 21:51:49 booklet-phyn3t NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> completed
Feb 23 21:52:56 booklet-phyn3t wpa_supplicant[944]: CTRL-EVENT-SCAN-RESULTS 
Feb 23 21:53:31 booklet-phyn3t avahi-daemon[734]: Invalid query packet.
Feb 23 21:53:31 booklet-phyn3t avahi-daemon[734]: Invalid query packet.
Feb 23 21:53:41 booklet-phyn3t kernel: [ 5097.661066] CE: hpet increasing min_delta_ns to 15000 nsec
thursdasy@booklet-phyn3t:~$ 

Feb 23 21:57:57 booklet-phyn3t wpa_supplicant[944]: WPA: Group rekeying completed with 00:19:e3:fa:28:8a [GTK=TKIP]
Feb 23 21:57:57 booklet-phyn3t NetworkManager: <info>  (wlan0): supplicant connection state:  completed -> group handshake
Feb 23 21:57:57 booklet-phyn3t NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> completed
Feb 23 21:58:31 booklet-phyn3t wpa_supplicant[944]: CTRL-EVENT-SCAN-RESULTS 
Feb 23 21:58:52 booklet-phyn3t pulseaudio[1594]: ratelimit.c: 2 events suppressed
Feb 23 21:58:58 booklet-phyn3t pulseaudio[1594]: ratelimit.c: 7 events suppressed
Feb 23 21:59:25 booklet-phyn3t pulseaudio[1594]: ratelimit.c: 1 events suppressed
Feb 23 22:00:03 booklet-phyn3t pulseaudio[1594]: ratelimit.c: 1 events suppressed
Feb 23 22:00:12 booklet-phyn3t wpa_supplicant[944]: CTRL-EVENT-SCAN-RESULTS 
Feb 23 22:00:59 booklet-phyn3t pulseaudio[1594]: ratelimit.c: 5 events suppressed


```

---

### Post by thursdasy on 2010-02-27
It seems I'm using the athk5 wifi drivers. Maybe madwifi would be a better choice?

---

### Post by msn0005 on 2010-03-23
Hey, have you fix the issue to the wifi yet? I seem to be having the same problem. The internet wont work but the wifi is still showing connected.

---

### Post by rolamento on 2010-04-29
I have the same problem. Any solution yet?

---

### Post by chenga91 on 2010-07-01
Same Problem here :(

---

