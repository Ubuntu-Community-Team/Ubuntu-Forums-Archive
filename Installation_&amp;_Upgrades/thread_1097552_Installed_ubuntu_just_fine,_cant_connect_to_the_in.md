---
title: "Installed ubuntu just fine, cant connect to the internet."
date: 2009-03-16
forum: Installation &amp; Upgrades
---

### Post by ac1dh0rse on 2009-03-16
I have an hp pavilion dv6000, I've tried going into the administration and networking windows and making my ethernet connection active but it still isn't working.

also if its any problem, right now I'm using the live cd, one of the things I wanted to do before I wiped xp was if I got it installed, make sure I was able to connect to the internet. I'm ready to take the dive so to speak and install it but I really wanna get this situation fixed before I do :(

---

### Post by sanemanmad on 2009-03-16
Hmmm... what does ```
ifconfig -a
``` show?

---

### Post by ac1dh0rse on 2009-03-16
> **sanemanmad said:**
> Hmmm... what does ```
ifconfig -a
``` show?

how do I find this? I'm sorry for such a dumb question but I know nothing of linux

---

### Post by delirejisor on 2009-03-16
open a terminal from 
applications-accesories-terminal

and write those to the terminal

---

### Post by ac1dh0rse on 2009-03-16
I had to type all of this out by hand D:

eth0   link encap: Ethernet   HWaddr 00:1B:24:49:76:4c
       inet6 addr: fe80::21b:24ff:fe49:764c/64 Scope: link
       UP BROADCAST RUNNING MULTICAST MTU:1500 Metric: 1
       RX packets:15767 errors:0 dropped:0 overruns:0 frame:0
       TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
       collisions:0 txqueuelen:1000
       RX bytes:1037469 (1013.1 KiB)  TX bytes:5040 (4.9 KiB)
       interupt: 10


If you need me to type what it says for lo and sit0 I can get working on those

---

### Post by ac1dh0rse on 2009-03-16
lo     link encap: local loopback
       inet addr:127.0.0.1  Mask:255.0.0.0
       UP LOOPBACK RUNNING MTU:16436 Metric:1
       RX packets:493 errors:0 dropped:0 overruns:0 frame:0
       TX packets:493 errors:0 dropped:0 overrunrs:0 carrier:0
       collisions:0 txqueuelen:0
       RX bytes:36640 (35.7 KiB) TX bytes:36640 (35.7 KiB)


sit0   Link encap: IPv6-in-IPv4
       NOARP MTU:1480 Metric:1
       RX packets:0 errors:0 dropped:0 overruns:0 frame:0
       TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
       Collisions:0 txqueuelen:0 
       RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)

---

### Post by sanemanmad on 2009-03-16
No that will not be necessary. Next time just right click, copy and paste :)


Try this in the terminal... 

```
sudo dhclient
```

How are you connecting to the internet? Wired / Wireless?

> No that will not be necessary. Next time just right click, copy and paste :)

I get it.... You are rebooting into working OS each time...

---

### Post by ac1dh0rse on 2009-03-16
nah, my laptop is sitting right next to me and im typing on my desktop. I'm trying to get a wired connection to the internet, once that starts working I'll figure out wireless.

I typed it and its going through the DHCDISCOVER on eth0 to 255.255.255.255.255 port 64 to different intervals, starting at 4 and ending at 12.

Now it said "no DHCPOFFERS received
no working leases in persistent database - sleeping.

---

### Post by sanemanmad on 2009-03-16
ok post this 

```
lspci
```
```

tail /var/log/syslog
```

---

### Post by sanemanmad on 2009-03-16
Might be a significant amount of output, , may want to consider transfer from pc's via thumb drive or some other

---

### Post by ac1dh0rse on 2009-03-16
is there any specific important part I should post or just the whole thing?

I'm without a thumb drive, and you were right, its a huge ammount of data

---

### Post by sanemanmad on 2009-03-16
```
lspci
```

> 01:08.0 Ethernet controller: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller

--or--

> 05:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller (rev 14) .... somewhere along these lines

And as far as > syslog goes, I am just curious if there are any errors reported that are specific to dhcp / networking

---

### Post by ac1dh0rse on 2009-03-16
I'm not seeing anything in the log as far as what ethernet card it has, so im guessing it doesn't see the card at all, which is what the problem is, and syslog is empty.

---

### Post by ac1dh0rse on 2009-03-16
I also tried 

ping -c 2 ubuntu.com and it says
ping: unknown host ubuntu.com

edit: upon closer inspection, when I went back to windows xp on the laptop (safemode with networking) i was not able to connect to the internet on windows xp at all.

so im thinking that it could be a virus or something thats making it so I cant connect to it at all.

---

### Post by sanemanmad on 2009-03-16
Hmmm.... Viruses on your Windows partition should not be affecting any hardware, especially when you are running a live linux cd. I would check that the ethernet port is working on both your local router and pc.

---

### Post by ac1dh0rse on 2009-03-16
> **sanemanmad said:**
> Hmmm.... Viruses on your Windows partition should not be affecting any hardware, especially when you are running a live linux cd. I would check that the ethernet port is working on both your local router and pc.

I'm just really confused and kinda frustrated.

---

### Post by ac1dh0rse on 2009-03-16
I switched the actual network thing to eth0 (the little monitor icons next to the clock) and when my cable is plugged in, it receives packets now, but I still get 404's.

---

### Post by sanemanmad on 2009-03-16
Ok, so now check a few settings, try dhclient eth0, check the route command

---

### Post by ac1dh0rse on 2009-03-16
says "can't create /var/lib/dhcp3/dhclient.leases: permission denied"
"cant create /var/run/dhclient.pid: permission denied
drop_privileges: could not set group id: operation not permitted"

closer and closer to solving this

---

### Post by ac1dh0rse on 2009-03-16
bump

---

### Post by sanemanmad on 2009-03-23
Make sure you are using "sudo" before each command. That is away of executing a command as the "administrator"

example: ```
sudo dhclient eth0
```

---

