---
title: "internet problems"
date: 2007-12-12
forum: Hardware &amp; Laptops
---

### Post by danmetiv on 2007-12-12
So I'm not very computer literate so please have patients with me.  I've put Ubuntu 6.06 on an old HP computer and it seems to work well, but I can't get online with it.  I've ran pppoeconf in the root menu, it says I have 1 ethernet interface (eth0), In network tools I can get it to transmit a few packets and recieve a few packets, but can't get anything on firefox.  What am I missing?

Thanks for any help.

---

### Post by Stemp on 2007-12-12
Open a terminal and try this command :

```
ping ubuntuforums.org
```

You should received something like that :

```
stemp@caderousse:~$ ping ubuntuforums.org
PING ubuntuforums.org (91.189.94.186) 56(84) bytes of data.
64 bytes from ohiggins.canonical.com (91.189.94.186): icmp_seq=1 ttl=50 time=57.6 ms
64 bytes from ohiggins.canonical.com (91.189.94.186): icmp_seq=2 ttl=50 time=57.8 ms

--- ubuntuforums.org ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1000ms
rtt min/avg/max/mdev = 57.669/57.777/57.885/0.108 ms

```

Hit Ctrl+C to stop the ping

---

