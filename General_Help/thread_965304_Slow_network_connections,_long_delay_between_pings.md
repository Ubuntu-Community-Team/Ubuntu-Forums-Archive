---
title: "Slow network connections, long delay between pings"
date: 2008-10-31
forum: General Help
---

### Post by szquirrel on 2008-10-31
A very odd problem: I went to play an old favorite flash game the other day and had serious problems connecting to the game server. For kicks, I tried pinging the server:

```

$ ping live.gamebrew.com
PING live.gamebrew.com (67.225.179.89) 56(84) bytes of data.
64 bytes from 67.225.179.89: icmp_seq=1 ttl=53 time=33.1 ms
64 bytes from 67.225.179.89: icmp_seq=2 ttl=53 time=30.9 ms
64 bytes from 67.225.179.89: icmp_seq=3 ttl=53 time=29.4 ms
64 bytes from 67.225.179.89: icmp_seq=4 ttl=53 time=29.7 ms
64 bytes from 67.225.179.89: icmp_seq=5 ttl=53 time=35.2 ms
^C64 bytes from 67.225.179.89: icmp_seq=6 ttl=53 time=29.5 ms

--- live.gamebrew.com ping statistics ---
6 packets transmitted, 6 received, 0% packet loss, time 25224ms
rtt min/avg/max/mdev = 29.435/31.316/35.205/2.163 ms
```

"That's odd," I thought. "The ping times look normal but the delay between them is much longer than one second, more like five seconds."

Then I tried it a couple of different ways:

```

$ ping 67.225.179.89
PING 67.225.179.89 (67.225.179.89) 56(84) bytes of data.
64 bytes from 67.225.179.89: icmp_seq=1 ttl=53 time=29.6 ms
64 bytes from 67.225.179.89: icmp_seq=2 ttl=53 time=30.0 ms
64 bytes from 67.225.179.89: icmp_seq=3 ttl=53 time=29.3 ms
64 bytes from 67.225.179.89: icmp_seq=4 ttl=53 time=31.4 ms
64 bytes from 67.225.179.89: icmp_seq=5 ttl=53 time=30.9 ms

--- 67.225.179.89 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4000ms
rtt min/avg/max/mdev = 29.363/30.293/31.422/0.806 ms

$ ping -n live.gamebrew.com
PING live.gamebrew.com (67.225.179.89) 56(84) bytes of data.
64 bytes from 67.225.179.89: icmp_seq=1 ttl=53 time=29.7 ms
64 bytes from 67.225.179.89: icmp_seq=2 ttl=53 time=29.9 ms
64 bytes from 67.225.179.89: icmp_seq=3 ttl=53 time=29.7 ms
64 bytes from 67.225.179.89: icmp_seq=4 ttl=53 time=29.7 ms
64 bytes from 67.225.179.89: icmp_seq=5 ttl=53 time=29.4 ms
^C
--- live.gamebrew.com ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4016ms
rtt min/avg/max/mdev = 29.495/29.740/29.940/0.142 ms
```

I know what you're going to say: DNS problem, right? Not so much:

```

$ time nslookup live.gamebrew.com
Server:		192.168.10.100
Address:	192.168.10.100#53

Non-authoritative answer:
Name:	live.gamebrew.com
Address: 67.225.179.89


real	0m0.026s
user	0m0.004s
sys	0m0.004s
```

Also I tried this on my MacBook running Tiger and it has no problems at all, not with pinging, not with playing the game.

Tried it again today at work, same problem. Except then I ssh'ed to a file server down the hall that runs Ubuntu with an older kernel and it had *no trouble at all* with the pings (can't really play the game over ssh though).

This is madness. I can't find anything anywhere on the web that even comes close to describing a problem like this.

To summarize:
[LIST]
[*]Pings (and other TCP traffic) get horribly delayed when trying to communicate with the server live.gamebrew.com.
[*]The problem doesn't exist when pinging the IP address or when using ping -n
[*]DNS server is responsive. Using nslookup is blazing fast.
[*]Adding live.gamebrew.com to /etc/hosts fixes the ping problem but not the responsiveness of the game. Not that this would be much of a solution anyway.
[*]Never seen anything like this before (e.g. ping ubuntu.com works fine).
[*]Problem exists on home machine: Ubuntu 8.04 AMD64 kernel 2.6.24-21. Does not exist on home machine: MacOS X Tiger.
[*]Problem exists on work machine: Ubuntu 8.10 x86 kernel 2.6.27-7. Does not exist on work machine: Ubuntu 8.04 x86 kernel 2.6.24-12.
[/LIST]

What the hell is going on here? It's driving me crazy. Thanks in advance.

---

### Post by noworry on 2008-11-02
I am also having the exact same problem - very slow internet connection, long delay between pings !!!

Could somebody please help??

PING google.com (209.85.171.99) 56(84) bytes of data.
64 bytes from cg-in-f99.google.com (209.85.171.99): icmp_seq=1 ttl=237 time=322 ms
64 bytes from cg-in-f99.google.com (209.85.171.99): icmp_seq=2 ttl=237 time=321 ms
64 bytes from cg-in-f99.google.com (209.85.171.99): icmp_seq=3 ttl=237 time=323 ms
64 bytes from cg-in-f99.google.com (209.85.171.99): icmp_seq=4 ttl=237 time=320 ms
^C64 bytes from cg-in-f99.google.com (209.85.171.99): icmp_seq=5 ttl=237 time=320 ms

--- google.com ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 33443ms
rtt min/avg/max/mdev = 320.253/321.577/323.228/1.213 ms

---

### Post by noworry on 2008-11-02
finally solved it !!!
The problem was because I was having vpnc installed and the /etc/resolv.conf entries were not removed after I disconnect vpn. 

The culprit was found to be "resolvconf" package.

After removing that package, it is working fine now.

---

### Post by szquirrel on 2008-11-03
I don't have resolvconf or vpnc installed. I am on a VPN but it's hardware-based (SonicWALL TZ150).

---

### Post by mdalacu on 2011-03-15
Same problem here, but no vpnc, only dns cacher.

---

