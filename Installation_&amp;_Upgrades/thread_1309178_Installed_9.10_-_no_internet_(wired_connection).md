---
title: "Installed 9.10 - no internet (wired connection)"
date: 2009-11-01
forum: Installation &amp; Upgrades
---

### Post by ~loa~ on 2009-11-01
I've just finished a clean install of ubuntu 9.10 (had 9.04 previously, worked fine) and am now unable to connect to the internet.

Here's the situation:
* The network connections icon says its connected.
* When I unplug the modem, network connections registers it's been disconnected.
* Firefox, update, software centre etc. don't connect - there's no error message, they just keep loading forever/timeout.
* Ping of ubuntu.com, google.com - 100% packets successful (but things like traceroute, whois don't function)
* I've reinstalled ubuntu, didn't help
* pppoeconf didn't work
* There are two other PC's on the network and they connect fine, so not a problem with the modem or anything

Connection info:
$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:13:d4:cb:cf:1a  
          inet addr:10.1.1.4  Bcast:10.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::213:d4ff:fecb:cf1a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:771 errors:0 dropped:0 overruns:0 frame:0
          TX packets:494 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:77393 (77.3 KB)  TX bytes:57267 (57.2 KB)
          Interrupt:23 Base address:0x6000

Any suggestions?

---

### Post by sanderj on 2009-11-01
What's your output of

```
mtr -n -c3 -r 4.4.4.4
```

The number of hops will tell you (hopefully) what's going on: the more hops, the better.
By using "-n", this test is not spoiled by a non-functioning name server.


```
ubuntu@ubuntu:~$ mtr -n -c3 -r 4.4.4.4
HOST: ubuntu                      Loss%   Snt   Last   Avg  Best  Wrst StDev
  1. 192.168.1.254                 0.0%     3    2.0   2.7   1.9   4.2   1.3
  2. 82.169.27.254                 0.0%     3   20.5  21.3  20.4  22.9   1.4
  3. 77.67.64.1                    0.0%     3   21.7  21.8  21.7  21.9   0.1
  4. 89.149.184.205                0.0%     3   22.5  22.3  21.5  22.8   0.7
  5. ???                          100.0     3    0.0   0.0   0.0   0.0   0.0
ubuntu@ubuntu:~$
``` 

Alternative for mtr is traceroute and tracepath:

```
ubuntu@ubuntu:~$ traceroute -n 4.4.4.4
traceroute to 4.4.4.4 (4.4.4.4), 30 hops max, 60 byte packets
 1  192.168.1.254  4.806 ms  4.623 ms  5.577 ms
 2  82.169.27.254  61.486 ms  61.623 ms  62.512 ms
 3  77.67.64.1  62.594 ms  62.764 ms  63.053 ms
 4  89.149.184.205  63.203 ms 89.149.186.201  63.487 ms 89.149.185.89  63.598 ms
 5  * * *
 6  * * *
 7  * * *
```

and

```
ubuntu@ubuntu:~$ tracepath -n 4.4.4.4
 1:  192.168.1.34      0.147ms pmtu 1500
 1:  192.168.1.254     5.441ms asymm  2 
 1:  192.168.1.254     2.097ms asymm  2 
 2:  82.169.27.254    36.676ms 
 3:  77.67.64.1       35.766ms asymm  5 
 4:  89.149.186.201   34.923ms asymm  6 
 5:  no reply
 6:  no reply
^C
ubuntu@ubuntu:~$
```

---

### Post by dzisler on 2009-11-01
I seem to be having the same problem I can connect via usb port but when I try and use the lan port on machine it says no network found. This worked fine before the upgrade and I know the router is working.My chip is RTL-8201CL. Sorry to piggy-back but it seems like we may have the same problem.

---

### Post by ~loa~ on 2009-11-01
...Now it doesn't even boot, back to 9.04 for me.  Thanks for the input sanderj

---

### Post by mhampson on 2009-11-01
I have exactly the same connection/non-connection issues as described by the first post, and I am very suspicious because I have the same symptoms:

(i) when 9.10 is installed as a guest in a VirtualBox on a perfectly happy internet-connected 9.04 host, and

(ii) when 9.10 is installed as an all-fresh installation on a laptop where it is replacing a perfectly happy 9.04 installation.

Both show "connected" from the Network Connections icon (the first as eth0, the second as a successful connection to the house wireless network) - the laptop can even access other computers on the home network! -  but both timeout with zero downloaded when attempting to connect to anything on the internet.

Here's that output you asked for - transferred from an unhappy live 9.10 session on the laptop to this contented 9.04 installation on the desktop via the house network(!):

ubuntu@ubuntu:~$ mtr -n -c3 -r 4.4.4.4
HOST: ubuntu                      Loss%   Snt   Last   Avg  Best  Wrst StDev
  1. 192.168.1.1                   0.0%     3    2.8   7.3   1.8  17.4   8.8
  2. 212.74.102.30                 0.0%     3  375.5 365.6 359.8 375.5   8.6
  3. 10.72.4.216                   0.0%     3  383.9 373.5 364.7 383.9   9.7
  4. 10.72.4.126                   0.0%     3  387.3 378.0 368.2 387.3   9.5
  5. 213.200.78.117                0.0%     3  380.2 374.1 371.1 380.2   5.2
  6. 89.149.185.73                 0.0%     3  387.1 375.4 361.6 387.1  12.9
  7. 213.200.77.130                0.0%     3  392.2 401.7 370.8 442.1  36.6
  8. ???                          100.0     3    0.0   0.0   0.0   0.0   0.0
ubuntu@ubuntu:~$

EDIT: Interesting! 9.10 on the laptop connects to the internet perfectly via my 3G phone. Does 9.10 not like my D-Link house router, even though 9.04 is fine with it? Or is it something else?

---

### Post by ta35 on 2009-11-01
I have a Dynalink 524 router and it works fine with 9.10. If you can access your home network but not the internet, could it be something with your ip-address settings? Have you checked Settings - Network connections? If you use dynamic ip:s you should have dhcp enabled.

I had a problem with wireless connection, but it was solved by installing a new driver with drivers -tool and configuring network settings.

---

### Post by ta35 on 2009-11-01
> **dzisler said:**
> I seem to be having the same problem I can connect via usb port but when I try and use the lan port on machine it says no network found. This worked fine before the upgrade and I know the router is working.My chip is RTL-8201CL. Sorry to piggy-back but it seems like we may have the same problem.

Have you tried installing a new driver in Administration - Drivers? Seems your network card is missing a driver.

---

### Post by sanderj on 2009-11-01
> **mhampson said:**
> 
Here's that output you asked for - transferred from an unhappy live 9.10 session on the laptop to this contented 9.04 installation on the desktop via the house network(!):

ubuntu@ubuntu:~$ mtr -n -c3 -r 4.4.4.4
HOST: ubuntu                      Loss%   Snt   Last   Avg  Best  Wrst StDev
  1. 192.168.1.1                   0.0%     3    2.8   7.3   1.8  17.4   8.8
  2. 212.74.102.30                 0.0%     3  375.5 365.6 359.8 375.5   8.6
  3. 10.72.4.216                   0.0%     3  383.9 373.5 364.7 383.9   9.7
  4. 10.72.4.126                   0.0%     3  387.3 378.0 368.2 387.3   9.5
  5. 213.200.78.117                0.0%     3  380.2 374.1 371.1 380.2   5.2
  6. 89.149.185.73                 0.0%     3  387.1 375.4 361.6 387.1  12.9
  7. 213.200.77.130                0.0%     3  392.2 401.7 370.8 442.1  36.6
  8. ???                          100.0     3    0.0   0.0   0.0   0.0   0.0
ubuntu@ubuntu:~$

EDIT: Interesting! 9.10 on the laptop connects to the internet perfectly via my 3G phone. Does 9.10 not like my D-Link house router, even though 9.04 is fine with it? Or is it something else?

Your mtr output looks good: you have IP-connectivity. Congrats! ;-)

Next step: is your DNS working? Test with

```
mtr -c3 -r ubuntu.com
```

My output:


```
sander@quirinius:~$ mtr -c3 -r ubuntu.com
HOST: quirinius                   Loss%   Snt   Last   Avg  Best  Wrst StDev
  1. 192.168.2.254                 0.0%     3    2.2   1.6   1.3   2.2   0.5
  2. 192.168.1.254                 0.0%     3    2.3   2.3   2.2   2.5   0.1
  3. 82-169-27-254.ip.telfort.nl   0.0%     3   21.1  21.0  20.6  21.3   0.3
  4. ae2.ams20.ip4.tinet.net       0.0%     3   23.0  28.3  22.2  39.7   9.8
  5. xe-2-2-0.ams10.ip4.tinet.net  0.0%     3   38.7  27.9  22.3  38.7   9.3
  6. xe-9-0-0.edge3.Amsterdam1.Le  0.0%     3   22.0  25.0  22.0  28.6   3.3
  7. ae-34-52.ebr2.Amsterdam1.Lev  0.0%     3   24.9  23.5  22.2  24.9   1.3
  8. ae-2-2.ebr2.London1.Level3.n  0.0%     3   33.0  39.7  33.0  52.9  11.5
  9. ae-100-100.ebr1.London1.Leve  0.0%     3   32.0  32.1  32.0  32.3   0.1
 10. ae-44-44.ebr2.London2.Level3  0.0%     3   36.5  36.9  34.4  39.9   2.8
 11. ae-26-56.car2.London2.Level3  0.0%     3   33.1  35.3  33.1  37.9   2.4
 12. gi1-0-1.oxygen.canonical.com  0.0%     3   32.8  38.5  32.8  49.1   9.2
 13. eth0.peumo.canonical.com      0.0%     3   32.8  33.0  32.8  33.3   0.3
 14. vostok.canonical.com          0.0%     3   35.4  33.4  32.2  35.4   1.8
sander@quirinius:~$

```

If that works OK, try the web http method:

```
wget ubuntu.com
```

My output:


```
sander@quirinius:~$ wget ubuntu.com
--2009-11-01 22:39:22--  http://ubuntu.com/
Resolving ubuntu.com... 91.189.94.156
Connecting to ubuntu.com|91.189.94.156|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: http://www.ubuntu.com/ [following]
--2009-11-01 22:39:22--  http://www.ubuntu.com/
Resolving www.ubuntu.com... 91.189.90.41
Connecting to www.ubuntu.com|91.189.90.41|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 17385 (17K) [text/html]
Saving to: `index.html.1'

100%[======================================>] 17,385      --.-K/s   in 0.08s   

2009-11-01 22:39:22 (207 KB/s) - `index.html.1' saved [17385/17385]

sander@quirinius:~$
```

---

### Post by dzisler on 2009-11-01
Ok smack me in the back of the head.....I should have known better. Works great now.
Thanks

---

### Post by mhampson on 2009-11-02
Scary! All that low-level stuff makes me nervous! I don't like to think of myself as a total noob: I've been playing with Linux for over a year; six months ago I went from having VirtualBox Linux on a Windows host to having VirtualBox Windows on a Linux host and I love it (Windows is only for 100% Word compatibility for filling in Word forms for other people and [sadly] for doing any colour printing as Epson Linux support is very, very poor; the Windows VirtualBox has no internet access, to keep it virus free and nag-free; my laptop is all Linux); and I have even developed my own Linux distribution, an unbreakable Ubuntu kiosk CD and/or PC-on-a-stick USB for cheap unbreakable diskless nodes in schools (every Windows machine is broken in its own unique way and the consequent waste of resources in schools is breathtaking) ... but all that low-level stuff still makes me nervous! I just want things to work!

I took out my old D-Link router and put in the Philips I had bought to replace it, and 9.10 worked straight away - both on the laptop and in the VirtualBox. For some reason, 9.04 was OK with D-Link and its settings, 9.10 wasn't.

Thanks for your time. I hope the discovery that it's something to do with something that has changed between 9.04 and 9.10, and might have something to do with D-Link (which is a bit notorious for non-compatibility issues, I think) is useful to somebody somewhere.

M.

---

### Post by 2912pwil on 2009-11-02
I had something similar (down to DLINK router not working but 3G dongle did) off a Live CD - see

[http://ubuntuforums.org/showthread.php?t=1306701](http://ubuntuforums.org/showthread.php?t=1306701)

- which was sorted by disabling IPv6 in Firefox.. weird!

Cheers!

2912pwil

---

### Post by eyrezer on 2009-11-04
I have the same problem as ~loa~, except I haven't managed to resolve the problem. Any suggestions?

daniel@daniel:~$ mtr -n -c3 -r 4.4.4.4
HOST: daniel          Loss%   Snt   Last   Avg  Best  Wrst StDev
  1. 10.1.1.1          0.0%     3   19.8  18.9  18.1  19.8   0.9
  2. 218.101.61.30     0.0%     3   87.4  87.3  85.7  88.7   1.5
  3. ???              100.0     3    0.0   0.0   0.0   0.0   0.0
  4. 203.98.50.1       0.0%     3   92.1  97.0  92.1 100.4   4.4
  5. 203.98.50.251     0.0%     3   99.3  98.5  97.7  99.3   0.8
  6. 203.167.233.10    0.0%     3   96.7  96.7  95.1  98.4   1.7
  7. 202.84.142.145    0.0%     3  224.1 225.5 222.4 230.0   4.0
  8. 202.84.251.170    0.0%     3  221.4 227.0 221.4 229.9   4.9
  9. 202.84.249.42     0.0%     3  238.8 238.6 237.2 239.7   1.3
 10. 202.84.251.126    0.0%     3  236.1 293.4 236.1 404.4  96.2
 11. ???              100.0     3    0.0   0.0   0.0   0.0   0.0

daniel@daniel:~$ mtr -c3 -r ubuntu.com
HOST: daniel           Loss%   Snt   Last   Avg  Best  Wrst StDev
  1. mygateway1.ar7     0.0%     3   20.9  16.6  12.9  20.9   4.0
  2. lo0.internet.ivpn.pe15.telst  0.0%     3  109.9  95.8  81.9 109.9  14.0
  3. ??? 

daniel@daniel:~$ wget ubuntu.com
--2009-11-04 19:50:22--  [http://ubuntu.com/](http://ubuntu.com/)
Resolving ubuntu.com... 1.0.0.0
Connecting to ubuntu.com|1.0.0.0|:80... failed: Connection timed out.
Retrying.

---

### Post by sanderj on 2009-11-04
> **eyrezer said:**
> 
daniel@daniel:~$ mtr -c3 -r ubuntu.com
HOST: daniel           Loss%   Snt   Last   Avg  Best  Wrst StDev
  1. mygateway1.ar7     0.0%     3   20.9  16.6  12.9  20.9   4.0
  2. lo0.internet.ivpn.pe15.telst  0.0%     3  109.9  95.8  81.9 109.9  14.0
  3. ??? 

daniel@daniel:~$ wget ubuntu.com
--2009-11-04 19:50:22--  [http://ubuntu.com/](http://ubuntu.com/)
Resolving ubuntu.com... 1.0.0.0
Connecting to ubuntu.com|1.0.0.0|:80... failed: Connection timed out.
Retrying.

Look at that last command, espicially

```
Resolving ubuntu.com... 1.0.0.0
```

That's not good: that's not the IP address of ubuntu.com. So your DNS is saying strange things. Are you in a VPN or so? Or on a corporate network, with only a proxy?

---

### Post by [deXter] on 2009-11-05
> **~loa~ said:**
> I've just finished a clean install of ubuntu 9.10 (had 9.04 previously, worked fine) and am now unable to connect to the internet.

Here's the situation:
* The network connections icon says its connected.
* When I unplug the modem, network connections registers it's been disconnected.
* Firefox, update, software centre etc. don't connect - there's no error message, they just keep loading forever/timeout.
* Ping of ubuntu.com, google.com - 100% packets successful (but things like traceroute, whois don't function)
* I've reinstalled ubuntu, didn't help
* pppoeconf didn't work
* There are two other PC's on the network and they connect fine, so not a problem with the modem or anything

Connection info:
$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:13:d4:cb:cf:1a  
          inet addr:10.1.1.4  Bcast:10.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::213:d4ff:fecb:cf1a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:771 errors:0 dropped:0 overruns:0 frame:0
          TX packets:494 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:77393 (77.3 KB)  TX bytes:57267 (57.2 KB)
          Interrupt:23 Base address:0x6000

Any suggestions?

Exact same problem, both with wired and wireless. I'm on a Sony VAIO VGN-CS17G with a D-Link DSL-G640T router. Has anyone found a solution for this? All other distros, OSes and even earlier versions of Ubuntu work just fine..

---

### Post by eyrezer on 2009-11-07
Ok, I did a clean install, and there is some improvement. It will now load some pages, but extremely slowly. This is the new output from those commands:

daniel@daniel-laptop:~$ mtr -n -c3 -r 4.4.4.4
HOST: daniel-laptop               Loss%   Snt   Last   Avg  Best  Wrst StDev
  1. 10.1.1.1                      0.0%     3    0.6   0.6   0.5   0.9   0.2
  2. 218.101.61.30                 0.0%     3   74.0  74.0  73.3  74.8   0.7
  3. ???                          100.0     3    0.0   0.0   0.0   0.0   0.0
  4. 203.98.50.1                   0.0%     3   86.6  86.8  86.6  87.0   0.2
  5. 203.98.50.251                 0.0%     3   88.3  90.0  86.2  95.5   4.9
  6. 203.167.233.10                0.0%     3   87.3  87.4  87.3  87.6   0.2
  7. 202.84.142.129                0.0%     3  214.3 212.5 211.4 214.3   1.6
  8. 202.84.251.170                0.0%     3  212.8 212.9 212.4 213.6   0.6
  9. 202.84.249.42                 0.0%     3  223.3 223.8 223.3 224.4   0.5
 10. 202.84.251.126                0.0%     3  225.2 225.4 224.9 226.1   0.6
 11. ???                          100.0     3    0.0   0.0   0.0   0.0   0.0

daniel@daniel-laptop:~$ mtr -c3 -r ubuntu.com
HOST: daniel-laptop               Loss%   Snt   Last   Avg  Best  Wrst StDev
  1. mygateway1.ar7                0.0%     3    0.5   0.5   0.4   0.7   0.1
  2. lo0.internet.ivpn.pe15.telst  0.0%     3   79.8  99.1  79.8 135.0  31.1
  3. ???                          100.0     3    0.0   0.0   0.0   0.0   0.0
  4. ie1-g-0-0-0.telstraclear.net  0.0%     3   86.4  87.0  86.2  88.4   1.2
  5. ge-0-2-0-1.xcore1.acld.telst  0.0%     3   86.7  86.7  86.6  86.8   0.1
  6. 203.167.233.10                0.0%     3   86.7  86.5  85.5  87.2   0.9
  7. i-3-1-2.wil-core02.bx.reach.  0.0%     3  211.9 212.2 211.9 212.4   0.2
  8. i-1-0-0.wil-core03.bi.reach.  0.0%     3  212.1 212.0 211.5 212.3   0.4
  9. i-10-0-0.sjc-core01.bi.reach  0.0%     3  224.0 224.2 223.7 224.8   0.6
 10. i-2-1.eqnx02.bi.reach.com     0.0%     3  224.2 224.3 223.9 225.0   0.5
 11. l3-peer.eqnx02.pr.reach.com   0.0%     3  224.1 224.2 223.8 224.6   0.4
 12. vlan89.csw3.SanJose1.Level3.  0.0%     3  232.3 231.0 226.1 234.8   4.5
 13. ae-84-84.ebr4.SanJose1.Level  0.0%     3  229.1 233.1 229.1 238.3   4.8
 14. ae-2.ebr4.NewYork1.Level3.ne  0.0%     3  295.6 297.5 293.9 303.0   4.9
 15. ae-84-84.csw3.NewYork1.Level  0.0%     3  293.6 300.9 293.6 304.8   6.3
 16. ae-81-81.ebr1.NewYork1.Level  0.0%     3  293.6 293.8 293.5 294.4   0.5
 17. ae-41-41.ebr2.London1.Level3 33.3%     3  363.7 363.7 363.6 363.7   0.1
 18. ae-100-100.ebr1.London1.Leve 33.3%     3  363.0 363.1 363.0 363.1   0.1
 19. ae-41-41.ebr2.London2.Level3 33.3%     3  375.9 369.7 363.5 375.9   8.7
 20. ae-26-54.car2.London2.Level3 33.3%     3  363.4 364.0 363.4 364.6   0.8
 21. gi1-0-1.oxygen.canonical.com 33.3%     3  362.7 363.8 362.7 364.9   1.6
 22. eth0.peumo.canonical.com     33.3%     3  363.2 363.3 363.2 363.4   0.2
 23. ubuntu.com                   33.3%     3  362.9 363.7 362.9 364.5   1.1

daniel@daniel-laptop:~$ wget ubuntu.com
--2009-11-08 08:25:12--  [http://ubuntu.com/](http://ubuntu.com/)
Resolving ubuntu.com... 91.189.94.156
Connecting to ubuntu.com|91.189.94.156|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: [http://www.ubuntu.com/](http://www.ubuntu.com/) [following]
--2009-11-08 08:25:13--  [http://www.ubuntu.com/](http://www.ubuntu.com/)
Resolving [www.ubuntu.com](www.ubuntu.com)... 91.189.90.40
Connecting to [www.ubuntu.com|91.189.90.40|:80](www.ubuntu.com|91.189.90.40|:80)... connected.
HTTP request sent, awaiting response... 200 OK
Length: 17385 (17K) [text/html]
Saving to: `index.html'

100%[======================================>] 17,385      20.4K/s   in 0.8s    

2009-11-08 08:25:15 (20.4 KB/s) - `index.html' saved [17385/17385]

---

### Post by sanderj on 2009-11-07
> **eyrezer said:**
> Ok, I did a clean install, and there is some improvement. It will now load some pages, but extremely slowly. 


<snip>
100%[======================================>] 17,385      20.4K/s   in 0.8s    

2009-11-08 08:25:15 (20.4 KB/s) - `index.html' saved [17385/17385]

All three outputs look OK, where the wget output (see quote above) indeed shows a 20 KB/s = 200 kbps = 0.2 Mbps download. Is that much less than your linespeed? If so, run the command below and measure again.


```
wget ftp://ftp.xs4all.nl/pub/test/10mb.bin

```

My output on my 11 Mbps line:


```
sander@quirinius:~$ wget ftp://ftp.xs4all.nl/pub/test/10mb.bin
--2009-11-07 08:16:52--  ftp://ftp.xs4all.nl/pub/test/10mb.bin
           => `10mb.bin'
Resolving ftp.xs4all.nl... 194.109.21.26
Connecting to ftp.xs4all.nl|194.109.21.26|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/test ... done.
==> SIZE 10mb.bin ... 10485760
==> PASV ... done.    ==> RETR 10mb.bin ... done.
Length: 10485760 (10M)

100%[======================================>] 10,485,760  1.01M/s   in 10s     

2009-11-07 08:17:03 (1020 KB/s) - `10mb.bin' saved [10485760]

sander@quirinius:~$

```

Conclusion: I get linespeed.

---

### Post by _Wolly_ on 2009-11-07
I experience the same internet problems after upgrading from 9.04 to 9.10.
Here my Output:
> 
wolly@wolly-desktop:~$ mtr -n -c3 -r 4.4.4.4
HOST: wolly-desktop               Loss%   Snt   Last   Avg  Best  Wrst StDev
  1. 192.168.1.1                   0.0%     3    3.5   3.5   3.5   3.6   0.1
  [COLOR=Red]2. ???                          100.0     3    0.0   0.0   0.0   0.0   0.0[/COLOR]
  3. 213.191.88.125                0.0%     3   27.6  27.4  27.0  27.6   0.4
  4. 213.191.87.165                0.0%     3   35.5  35.3  34.6  35.7   0.6
  5. 62.109.109.240                0.0%     3   34.8  35.9  34.8  37.3   1.3
  6. 195.22.211.113                0.0%     3   35.9  35.5  34.6  35.9   0.7
  [COLOR=Red]7. ???                          100.0     3    0.0   0.0   0.0   0.0   0.0[/COLOR]
> 
wolly@wolly-desktop:~$ mtr -c3 -r ubuntu.com
HOST: wolly-desktop               Loss%   Snt   Last   Avg  Best  Wrst StDev
  1. alice.box                     0.0%     3    5.2   4.1   3.4   5.2   1.0
  [COLOR=Red]2. lo1.br12.muc.de.hansenet.net **33.3%**     3   27.0  27.6  27.0  28.2   0.8[/COLOR]
  3. ae1-102.cr01.muc.de.hansenet  0.0%     3   28.1  27.8  27.2  28.1   0.5
  4. so-0-0-0-0.cr01.fra.de.hanse  0.0%     3   35.3  37.0  35.3  39.3   2.1
  5. ae0-0.pr03.decix.de.hansenet  0.0%     3   35.0  34.9  34.5  35.3   0.4
  6. ge0-1-0-cr0.ixf.de.as6908.ne  0.0%     3   36.8  35.9  35.4  36.8   0.7
  7. te1-4-3503-cr0.tch.uk.as6908  0.0%     3  148.8  82.2  48.8 148.8  57.6
  8. canonical-gw.gwr.datahop.net  0.0%     3   48.6  48.4  47.8  49.0   0.6
  9. eth0.peumo.canonical.com      0.0%     3   53.6  55.6  53.6  57.1   1.8
 10. vostok.canonical.com          0.0%     3   53.7  53.8  53.2  54.4   0.6
> 
wolly@wolly-desktop:~$ wget ubuntu.com
--2009-11-07 16:04:59--  [http://ubuntu.com/](http://ubuntu.com/)
Resolving ubuntu.com... 91.189.94.156
Connecting to ubuntu.com|91.189.94.156|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: [http://www.ubuntu.com/](http://www.ubuntu.com/) [following]
--2009-11-07 16:05:20--  [http://www.ubuntu.com/](http://www.ubuntu.com/)
Resolving [www.ubuntu.com]("http://www.ubuntu.com")... 91.189.90.41
Connecting to [www.ubuntu.com|91.189.90.41|:80]("http://www.ubuntu.com%7C91.189.90.41%7C:80")... connected.
HTTP request sent, awaiting response... 200 OK
Length: 17385 (17K) [text/html]
Saving to: `index.html'

100%[=====================================================================================================================================================================>] 17,385      --.-K/s   in 0.1s    

2009-11-07 16:05:40 (171 KB/s) - `index.html' saved [17385/17385]
Any ideas what causes these delays?

---

### Post by eyrezer on 2009-11-08
I've managed to get the internet working by disabling IPv6, which is good. However, I can't activate repositories etc, as it keeps saying the connection timed out. It also seems to have gone backwards to this:

daniel@daniel:~$ wget ubuntu.com
--2009-11-04 19:50:22-- [http://ubuntu.com/](http://ubuntu.com/)
Resolving ubuntu.com... 1.0.0.0
Connecting to ubuntu.com|1.0.0.0|:80... failed: Connection timed out.
Retrying.

---

### Post by jeekay on 2009-11-08
I have the same problem... Sorry to piggyback...  But thought it might be better to do that instead of making a new post. 
 
I got web browsing enabled by disabling ipv6 in firefox.([http://www.joehacker.com/index.php?title=Ubuntu_Tips#Disable_IPv6_on_Karmic_9.10](http://www.joehacker.com/index.php?title=Ubuntu_Tips#Disable_IPv6_on_Karmic_9.10)). 

So I figured that the issue may be with ipv6 not being supported by either my ISP, or my ancient DSL router (Huawei WA1003A).  So I went with the rest of the suggestions in the above page and tried disabling ipv6 for the whole OS.

But still no joy.  I am not able to update repositories and install any software.

The output of the commands mentioned above:
leggie@LeggiesDesktop:~$ mtr -n -c3 -r 4,4,4,4
Couldn't get fd's flags: Bad file descriptor
Name or service not known: No such file or directory
leggie@LeggiesDesktop:~$ mtr -n -c3 -r 4.4.4.4
Couldn't get fd's flags: Bad file descriptor
HOST: LeggiesDesktop              Loss%   Snt   Last   Avg  Best  Wrst StDev
  1. ???                          100.0     3    0.0   0.0   0.0   0.0   0.0
  2. 59.92.128.1                   0.0%     3   33.6  35.2  33.6  38.1   2.5
  3. 218.248.255.82                0.0%     3   39.0  38.2  37.8  39.0   0.6
  4. 218.248.246.130               0.0%     3   52.6  52.5  52.3  52.6   0.2
  5. ???                          100.0     3    0.0   0.0   0.0   0.0   0.0

leggie@LeggiesDesktop:~$ mtr -c3 -r ubuntu.com
Couldn't get fd's flags: Bad file descriptor
HOST: LeggiesDesktop              Loss%   Snt   Last   Avg  Best  Wrst StDev
  1. ???                          100.0     3    0.0   0.0   0.0   0.0   0.0
  2. 59.92.128.1                   0.0%     3   34.9  34.3  33.9  34.9   0.6
  3. 218.248.255.82                0.0%     3   37.8  37.9  37.8  38.1   0.2
  4. AES-Static-145.42.22.125.air  0.0%     3  107.3 108.4 106.8 111.0   2.3
  5. ???                          100.0     3    0.0   0.0   0.0   0.0   0.0
leggie@LeggiesDesktop:~$ wget ubuntu.com
--2009-11-08 19:51:17--  [http://ubuntu.com/](http://ubuntu.com/)
Resolving ubuntu.com... 1.0.0.0
Connecting to ubuntu.com|1.0.0.0|:80... failed: Connection timed out.
Retrying.

---

### Post by leeg on 2009-11-08
i'm also having the same problem firefox works but can't connet to repos

---

### Post by Giantmundo on 2009-11-15
My father is in the same boat.  Firefox works fine now that ipv6 is disabled but can't use update manager or Thunderbird.  I heard that network manager was broken and a patch released but can't locate it.  Any advice would be appreciated.  P.S. - My upgrade went fine.

---

### Post by jeekay on 2009-11-17
I followed the link in the post [http://newyork.ubuntuforums.org/showpost.php?p=8271657&postcount=16](http://newyork.ubuntuforums.org/showpost.php?p=8271657&postcount=16).  It worked for me.  After that mozilla worked without having to disable ipv6.  The sources also got updated and synaptic also started working.

However, I wonder why it doesnt work with the dns supplied by my router.  Why is is there a problem only with Ubuntu?  I have no issues with Windows XP, SUSE and FEDORA.  This issue seems to be there from version 7.10...

---

### Post by lesleytitus on 2009-11-17
> **jeekay said:**
> I followed the link in the post [http://newyork.ubuntuforums.org/showpost.php?p=8271657&postcount=16](http://newyork.ubuntuforums.org/showpost.php?p=8271657&postcount=16).  It worked for me.  After that mozilla worked without having to disable ipv6.  The sources also got updated and synaptic also started working.

However, I wonder why it doesnt work with the dns supplied by my router.  Why is is there a problem only with Ubuntu?  I have no issues with Windows XP, SUSE and FEDORA.  This issue seems to be there from version 7.10...

OK that helped the browsing issue, you mentioned that the source has the solution to the update manager also...i don't see any other link anywhere...

But thanks my browsing is back to normal... has anyone found the answer to this majorly irritating problem?

UPDATE: SORRY MATE, found the link to the forum (top right, lol), but still there is no solution for thus problem, all they have done is fix up their internet....

---

### Post by jeekay on 2009-11-17
Harcoding the DNS solved both the 'browsing with Mozilla Firefox' and the 'updating repositories and installing packages with synaptic package manager' problems for me.

---

### Post by Commander_Bob on 2009-11-25
I'm having a similar problem, clean install of 9.10, was running 9.04 and now I have no internet. I'm using a Dell Mini9.

I connected the wired internet, and issueed the command.
> **sanderj said:**
> What's your output of
```
mtr -n -c3 -r 4.4.4.4
```

```
No nameservers defined.
```

What is going on?

---

### Post by bonka on 2009-11-25
Commander Bob, I have the same problem...

I have connected my other laptop to the router (windows vista laptop), works fine, my dell mini 9, same error message as you got via the terminal

Does anyone have any idea???

[http://www.ubuntumini.com](http://www.ubuntumini.com) doesn't help either

---

### Post by sanderj on 2009-11-25
> **Commander_Bob said:**
> I'm having a similar problem, clean install of 9.10, was running 9.04 and now I have no internet. I'm using a Dell Mini9.

I connected the wired internet, and issueed the command.

```
No nameservers defined.
```

What is going on?

So it's a nameserver problem. I can't check right now, but I believe the nameserver is defined in /etc/resolv.conf

So post the output of "cat /etc/resolv.conf"

---

### Post by bonka on 2009-11-26
The error message that I receive is "No such file/directory"

did you mean "cat /etc/resolvconf/", this provides "is a directory"

---

### Post by Commander_Bob on 2009-11-26
Same deal with me, no resolv.conf file but a resolvconf directory that has another folder, update-libc.d, and in that folder one file, avahi-deamon.

---

### Post by sanderj on 2009-11-26
No /etc/resolv.conf ?! I would say *that* *is* the problem. 

See my output below. 

Is your IP-network working at all? Check with the ifconfig command below and "mtr -n -c3 -r 4.4.4.4"



ubuntu@ubuntu:~$ cat /etc/resolv.conf 
# Generated by NetworkManager
domain lokaal
search lokaal
nameserver 192.168.1.254
nameserver 195.241.77.55
nameserver 195.241.77.58
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ uname -a
Linux ubuntu 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686 GNU/Linux
ubuntu@ubuntu:~$ 

ubuntu@ubuntu:~$ ifconfig | grep -i inet
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          inet addr:192.168.1.34  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::218:deff:fe10:c506/64 Scope:Link
ubuntu@ubuntu:~$

---

### Post by sanderj on 2009-11-26
I just discovered that without a nameserver defined (or working?), mtr does not work, even not with -n. IMHO, that's a bug.

For a better IP connectivity check, even with no nameserver working, use tracepath -n, for example "tracepath -n  4.4.4.4". See below.

```

ubuntu@ubuntu:~$ mtr -r -c1 -n 4.4.4.4
No nameservers defined.


ubuntu@ubuntu:~$ tracepath -n  4.4.4.4
 1:  192.168.1.34      0.214ms pmtu 1500
 1:  192.168.1.254     2.577ms asymm  2 
 1:  192.168.1.254     1.940ms asymm  2 
 2:  82.169.27.254    31.433ms 
 3:  193.172.66.193   35.751ms asymm  5 
 4:  195.190.227.223  34.971ms asymm  6 
 5:  134.222.231.202  43.137ms asymm  6 
 6:  134.222.231.197  45.376ms asymm  7 
 7:  no reply
 8:  no reply
^C
ubuntu@ubuntu:~$


```

---

### Post by triplemaya on 2009-11-26
Many thanks jeekay, the link you provided

I followed the link in the post [http://newyork.ubuntuforums.org/show...7&postcount=16](http://newyork.ubuntuforums.org/show...7&postcount=16). It worked for me. 

worked for me.

I had a new install of 9.10 remix, good wireless connection, but firefox couldn't see the internet, and no updates working. Now it's all good.

Solved

Cheers

---

### Post by bonka on 2009-11-27
the mtr command provides "No nameserves defined."

the ifconfig gives the following:

Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:4 errors:0 dropped:0 overruns:0 frame:0
TX packets:4 errors:0 dropped:0 ovveruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:240 (240.0 B) TX bytes:240 (240.0 B)

---

### Post by bonka on 2009-11-27
> **triplemaya said:**
> Many thanks jeekay, the link you provided

I followed the link in the post [http://newyork.ubuntuforums.org/show...7&postcount=16](http://newyork.ubuntuforums.org/show...7&postcount=16). It worked for me. 

worked for me.

I had a new install of 9.10 remix, good wireless connection, but firefox couldn't see the internet, and no updates working. Now it's all good.

Solved

Cheers

Link doesn't work.... Could you please post again???

---

### Post by bonka on 2009-11-27
okay with the line in the terminal:

tracepath -n 4.4.4.4

I get the following:

1:   send failed
     Resume: pmtu 65535

---

### Post by sanderj on 2009-11-27
> **bonka said:**
> the mtr command provides "No nameserves defined."

the ifconfig gives the following:

Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:4 errors:0 dropped:0 overruns:0 frame:0
TX packets:4 errors:0 dropped:0 ovveruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:240 (240.0 B) TX bytes:240 (240.0 B)

You have no (LAN/WAN) IP address. So solve that first: connect to your LAN. A wired connection is easier to establish than a wireless connection. So connect your ethernet cable, and run ifconfig again.

---

### Post by scott dillon on 2009-11-27
> **dzisler said:**
> Ok smack me in the back of the head.....I should have known better. Works great now.
Thanks
Hi There,
i have recently successfully installed ubuntu on my  PC and now I do not have internet connection. I was using windows but partitoned the PC. I am using a belkin wireless usb adapter. I have think I need a belkin driver but unable to find one. Would you possibly know how I can get the connection to work?
 
Best Regards,
Scott.

---

### Post by bonka on 2009-11-27
> **sanderj said:**
> You have no (LAN/WAN) IP address. So solve that first: connect to your LAN. A wired connection is easier to establish than a wireless connection. So connect your ethernet cable, and run ifconfig again.

I have been running the commands with the LAN cable plugged in. I also tried another laptop (vista) works fine on the LAN connection. Any chance this could be an issue wuth an option in the router? I have a dlink DSL-2740B

---

### Post by sanderj on 2009-11-27
> **bonka said:**
> I have been running the commands with the LAN cable plugged in.

And ... what is the output of the commands?

---

### Post by drjonze on 2009-11-27
I hate to say it but I get the feeling that 9.10 was rushed. So many network/internet issues. For an OS trying to prove its ready for prime time, having internet issues is a bad start.

Don't get me wrong, I love Ubuntu, I'm still using it but I have never had any internet issues with the 5 other releases I have tried. I may have to dial back to a previous version. 

I can put up with a lot of bugs and glitches but not when it comes to an internet connection. Its like having a car with no gas. Its the one area I will not compromise on. It just has to work.

---

### Post by Giantmundo on 2009-11-29
I have resolved my father's problems.  He wasn't able to get any internet at all. It appeared he was timing out.  There were two things that eventually resolved his issues.  IPv6 and DNS.

With IPv6 there were three things that I did to disable it.  Firefox, Thunderbird and the system itself.

With Firefox and Thunderbird it was simply a case of disabling IPv6 via the config options.  This had instant success and he was able to browse the net and get email.  Email was important so I could provide my dear old Dad, a 74 yr old Ubuntu man, the necessary terminal commands to achieve the next fixes.

I gave him the essentials from this web page to disable IPv6 for the system itself.  This didn't help initially but I feel he got a result once the DNS issue was resolved.
[http://www.webupd8.org/2009/05/how-to-disable-ipv6-in-ubuntu-jaunty.html]("http://www.webupd8.org/2009/05/how-to-disable-ipv6-in-ubuntu-jaunty.html")

As for DNS I didn't really want get involved with altering the grub. So as mentioned in other posts on this thread I got him to do what was suggested in this two year old thread and everything is back to normal and working.
[http://ubuntuforums.org/showpost.php?p=3996845&postcount=5]("http://ubuntuforums.org/showpost.php?p=3996845&postcount=5")

This took a few weeks to sort out. I do have other people and things to look after.  The unfortunate thing about it all is that he will not now get rid of his XP partition.  That was the plan.  Get Karmic and consider a new install and use XP via Virtualbox.  The update was a transition step so to speak.

I talked to Dad about the LTS releases versus the risk of the bleeding edge releases.  In his case stability is important but then again he has me to help him through.  Silly me.

As others have said I just wish that Canonical would ensure that certain basic system functions are rock solid.  Plug and play internet would have to be very high on the list.

Good luck to everyone else that have found themselves in a similar situation with the Karmic upgrade.

---

### Post by 2912pwil on 2009-11-29
Further to my earlier...

Been playing around with a new router (3g, Edimax as it happens) and having got that up 'n running thought I'd try the LiveCd again (64bit 9.10).. 

Booted:
Start Firefox...
Out onto the Internet, straight away, no playing around with parameters in Firefox or anything else, no problem...yippeee!!

So,,,, it looks like the "problem" is some issue/incompatibility between 9.10 and some routers (certainly in my case the D-Link DSL-G624T).

Hope that helps someone else...

Now to install 9.10 & have a proper go!!

---

### Post by Nightstrike2009 on 2009-11-29
> **By Giantmundo:** As others have said I just wish that Canonical would ensure that certain basic system functions are rock solid. Plug and play internet would have to be very high on the list.

Good luck to everyone else that have found themselves in a similar situation with the Karmic upgrade.

I too had to downgrade to Ubuntu 9.04 after finding my 3G Vodafone Modem & bluetooth borked with Ubuntu 9.10. I lost some converts to Linux due to this massive oversight (and the bug was reported before release). 

I am so disgusted that Ubuntu 9.10 was rushed out with major flaws in it, I have migrated to Linux Mint 7 (As Linux Mint 8 is based on Ubuntu 9.10 i'd rather avoid it).

Congratulations I was an Ubuntu convert and swore by it. This recent behaviour (Buggy rushed out OS's is the reason I was drawn To Linux from Windows) I love linux and will continue to use it In future I will exercise a lot caution before installing any future Ubuntu Release, this kind of behaviour makes MS look good and Linux look bad.

Not welcome and not needed as Windows7 only just released. :(

---

### Post by morcar on 2009-12-06
I dunno about this problem as i went from Jaunty 9.04 and upgraded to the new 9.10 and i had no problems. Maybe thats a way around it.

I know later versions like Version 8 I couldnt get online for love or money.

---

### Post by 2912pwil on 2009-12-12
Just a re-confirmation:  Tried an old "GURU" ADSL router on the 9.10 32b live CD:  Internet access straight-away, on problems, whereas I did have problems getting out using my normal D-Link router:

Looks like there is a compatibility issue somewhere with some Routers & 9.10

Regards

2912

---

### Post by sanderj on 2009-12-12
> **2912pwil said:**
> 

Looks like there is a compatibility issue somewhere with some Routers & 9.10


I have no delays myself so I can't test it, but it could be a DNS thing. Hypothesis Ubuntu 9.10 talking to the DNS in the router can be slow.

If you experience the slowness on your system, can you run the one-liner 

```
cat /etc/resolv.conf | grep nameserver | awk '{ print "time dig +short www.xs4all.nl @" $2 }' | /bin/sh
```


and post the output here?

See [http://ubuntuforums.org/showpost.php?p=8400666&postcount=13](http://ubuntuforums.org/showpost.php?p=8400666&postcount=13)

---

### Post by 2912pwil on 2009-12-19
Thanks...re..
> and post the output here?

Having finally upgraded to 9.10 using my "GURU" router, all worked fine, then reverting to the "D-Link" Router no internet access: Can (still) get Firefox running if I disable IPv6 with about:config but nothing else (eg "Update Manager") works...
I get 

> phillip@phillip-laptop:~$ cat /etc/resolv.conf | grep nameserver | awk '{ print "time dig +short [www.xs4all.nl](www.xs4all.nl) @" $2 }' | /bin/sh
194.109.6.92
0.00user 0.00system 0:00.09elapsed 8%CPU (0avgtext+0avgdata 0maxresident)k
408inputs+0outputs (2major+799minor)pagefaults 0swaps


Regards & thanks in advance...

2912pwil

---

### Post by editdigital on 2009-12-19
> **mhampson said:**
> Scary! All that low-level stuff makes me nervous! I don't like to think of myself as a total noob: I've been playing with Linux for over a year; six months ago I went from having VirtualBox Linux on a Windows host to having VirtualBox Windows on a Linux host and I love it (Windows is only for 100% Word compatibility for filling in Word forms for other people and [sadly] for doing any colour printing as Epson Linux support is very, very poor; the Windows VirtualBox has no internet access, to keep it virus free and nag-free; my laptop is all Linux); and I have even developed my own Linux distribution, an unbreakable Ubuntu kiosk CD and/or PC-on-a-stick USB for cheap unbreakable diskless nodes in schools (every Windows machine is broken in its own unique way and the consequent waste of resources in schools is breathtaking) ... but all that low-level stuff still makes me nervous! I just want things to work!

I took out my old D-Link router and put in the Philips I had bought to replace it, and 9.10 worked straight away - both on the laptop and in the VirtualBox. For some reason, 9.04 was OK with D-Link and its settings, 9.10 wasn't.

Thanks for your time. I hope the discovery that it's something to do with something that has changed between 9.04 and 9.10, and might have something to do with D-Link (which is a bit notorious for non-compatibility issues, I think) is useful to somebody somewhere.

M.


I've to have the same problem. I used to have a happly ubuntu 9.04 Jaunty system with perfectly functioning DSL dialup, but now after installing 9.10 Karmic, I'm unable to initiate a DSL connection,, I have to go the iBall Baton router page to dial from the router.

---

### Post by bayvista on 2009-12-20
I am running 9.10 through a D-Link ADSL Router (DSL502T) and a Wireless Router (DI524). Both work fine. However, I am using a fixed IP address which I setup by editing /etc/network/interfaces from info in this forum. I am not using the Network Manager which appears on the rhs of the top panel.

I always disable ipv6.

---

### Post by 2912pwil on 2009-12-21
> 
I always disable ipv6.

Thanks... I know how to disable IPv6 in firefox but not for all of the system - any easy/simple instructions anyone knows of for doing this??

Regards & Thanks in advance..

2912pwil

---

### Post by bayvista on 2009-12-22
Just google "ubuntu disable ipv6" and you will get some ideas. I used the 'blacklist' solution and this works fine.

How's the snow?

---

### Post by Stefano85 on 2009-12-22
I have the same kind of issues described in the post. However, when i type in the command mtr -c3 -r 4.4.4.4 i get a no nameservers defined... I'm not an expert in networking so I'm a bit puzzled.. any help is welcome..thanks!!

---

### Post by sanderj on 2009-12-22
> **Stefano85 said:**
> no nameservers defined

That's bad! Do you have a network connection at all? Post the output of "ifconfig" here.

---

