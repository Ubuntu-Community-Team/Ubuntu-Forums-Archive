---
title: "Headless system becoming unresponsive on network"
date: 2008-08-27
forum: General Help
---

### Post by KrisWillis on 2008-08-27
I have an install of 8.04 running on a headless machine that is used as a media server. Every couple of days, sometimes weeks, the machine becomes unresponsive - Its mt-daapd share disappears from all of my clients that access it, web requests time out (running Apache2), attempts to connect over SSH time out and I cannot access any SAMBA shares.

The only way to regain access is to hit the reset button and wait for it to boot. It is very inconvenient for me to hook up a monitor to it due to where it is located, but is there any logs I can check after rebooting that might give some insight as to what is causing this?

The machine is set to maintain a static IP, although my router has DHCP enabled, the assignable IP range starts above my static IP.

My /etc/network/interfaces file looks like this:
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.113
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1
```

I'm assuming this is how I set the machine to have a static IP, after all, I can connect to it until it drops off of the network. I'm fairly sure it's not tied to inactivity either as it has disappeared halfway through streaming video before. Any insight into my problem would be great!

Many thanks.

---

### Post by cariboo on 2008-08-27
You may have a flaky network card or network cable. I was having the same problem with my server, replacing the network card solved the problem.

Jim

---

### Post by KrisWillis on 2008-08-28
Interesting suggestion - I'm not sure why I immediatly jumped on the fact that it must be software related... I'll dig out a NIC and throw it in there and see what happens, plus hook a cable tester up to the wall plate and cable.

Will report back with results.

---

