---
title: "[SOLVED] Synaptic not working - dkpg broken"
date: 2008-11-27
forum: General Help
---

### Post by Bödvar on 2008-11-27
When trying to get updates or install things with synaptic, my computer tells me:

```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
```

So I write in terminal:

```
sudo dpkg --configure -a
```

And it is now doing a lot of work, I will post what it says later.

My question is: what on earth is this? Why does it happen? Why did it break and why does it need to do all these commands suddenly? I can't install .deb packages, use add/remove, or synaptic. Even "apt-get install blabla" in terminal won't work. Will this fix it?

All information regarding this will be appreciated. Thanks!

---

### Post by Bödvar on 2008-11-27
So this is what happened. It is finished now:

```

following]
--2008-11-27 12:29:20--  http://surfnet.dl.sourceforge.net/sourceforge/corefonts/arialb32.exe
Connecting to surfnet.dl.sourceforge.net|130.59.138.20|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://prdownloads.sourceforge.net/corefonts/arialb32.exe?download&failedmirror=surfnet.dl.sourceforge.net [following]
--2008-11-27 12:29:20--  http://prdownloads.sourceforge.net/corefonts/arialb32.exe?download&failedmirror=surfnet.dl.sourceforge.net
Connecting to prdownloads.sourceforge.net|216.34.181.60|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://nchc.dl.sourceforge.net/sourceforge/corefonts/arialb32.exe [following]
--2008-11-27 12:29:21--  http://nchc.dl.sourceforge.net/sourceforge/corefonts/arialb32.exe
Resolving nchc.dl.sourceforge.net... 211.79.60.17
Connecting to nchc.dl.sourceforge.net|211.79.60.17|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 168176 (164K) [application/x-msdownload]
Saving to: `./arialb32.exe'

100%[======================================>] 168,176     39.3K/s   in 4.2s    

2008-11-27 12:29:26 (39.5 KB/s) - `./arialb32.exe' saved [168176/168176]

--2008-11-27 12:29:26--  http://surfnet.dl.sourceforge.net/sourceforge/corefonts/arial32.exe
Resolving surfnet.dl.sourceforge.net... 130.59.138.20
Connecting to surfnet.dl.sourceforge.net|130.59.138.20|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://prdownloads.sourceforge.net/corefonts/arial32.exe?download&failedmirror=surfnet.dl.sourceforge.net [following]
--2008-11-27 12:29:26--  http://prdownloads.sourceforge.net/corefonts/arial32.exe?download&failedmirror=surfnet.dl.sourceforge.net
Resolving prdownloads.sourceforge.net... 216.34.181.60
Connecting to prdownloads.sourceforge.net|216.34.181.60|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://nchc.dl.sourceforge.net/sourceforge/corefonts/arial32.exe [following]
--2008-11-27 12:29:27--  http://nchc.dl.sourceforge.net/sourceforge/corefonts/arial32.exe
Resolving nchc.dl.sourceforge.net... 211.79.60.17
Connecting to nchc.dl.sourceforge.net|211.79.60.17|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 554208 (541K) [application/x-msdownload]
Saving to: `./arial32.exe'

100%[======================================>] 554,208     39.3K/s   in 14s     

2008-11-27 12:29:41 (39.4 KB/s) - `./arial32.exe' saved [554208/554208]

--2008-11-27 12:29:41--  http://surfnet.dl.sourceforge.net/sourceforge/corefonts/comic32.exe
Resolving surfnet.dl.sourceforge.net... 130.59.138.20
Connecting to surfnet.dl.sourceforge.net|130.59.138.20|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://prdownloads.sourceforge.net/corefonts/comic32.exe?download&failedmirror=surfnet.dl.sourceforge.net [following]
--2008-11-27 12:29:42--  http://prdownloads.sourceforge.net/corefonts/comic32.exe?download&failedmirror=surfnet.dl.sourceforge.net
Resolving prdownloads.sourceforge.net... 216.34.181.60
Connecting to prdownloads.sourceforge.net|216.34.181.60|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://umn.dl.sourceforge.net/sourceforge/corefonts/comic32.exe [following]
--2008-11-27 12:29:43--  http://umn.dl.sourceforge.net/sourceforge/corefonts/comic32.exe
Resolving umn.dl.sourceforge.net... 128.101.240.209
Connecting to umn.dl.sourceforge.net|128.101.240.209|:80... connected.
HTTP request sent, awaiting response... 504 Gateway Timeout
2008-11-27 12:30:59 ERROR 504: Gateway Timeout.

--2008-11-27 12:30:59--  http://mesh.dl.sourceforge.net/sourceforge/corefonts/comic32.exe
Resolving mesh.dl.sourceforge.net... 213.203.218.122
Connecting to mesh.dl.sourceforge.net|213.203.218.122|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://prdownloads.sourceforge.net/corefonts/comic32.exe?download&failedmirror=mesh.dl.sourceforge.net [following]
--2008-11-27 12:31:00--  http://prdownloads.sourceforge.net/corefonts/comic32.exe?download&failedmirror=mesh.dl.sourceforge.net
Resolving prdownloads.sourceforge.net... 216.34.181.60
Connecting to prdownloads.sourceforge.net|216.34.181.60|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://mesh.dl.sourceforge.net/sourceforge/corefonts/comic32.exe [following]
--2008-11-27 12:31:00--  http://mesh.dl.sourceforge.net/sourceforge/corefonts/comic32.exe
Connecting to mesh.dl.sourceforge.net|213.203.218.122|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://prdownloads.sourceforge.net/corefonts/comic32.exe?download&failedmirror=mesh.dl.sourceforge.net [following]
--2008-11-27 12:31:01--  http://prdownloads.sourceforge.net/corefonts/comic32.exe?download&failedmirror=mesh.dl.sourceforge.net
Reusing existing connection to prdownloads.sourceforge.net:80.
HTTP request sent, awaiting response... 302 Found
Location: http://master.dl.sourceforge.net/sourceforge/corefonts/comic32.exe [following]
--2008-11-27 12:31:02--  http://master.dl.sourceforge.net/sourceforge/corefonts/comic32.exe
Resolving master.dl.sourceforge.net... 216.34.181.56
Connecting to master.dl.sourceforge.net|216.34.181.56|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 246008 (240K) [application/octet-stream]
Saving to: `./comic32.exe'

100%[======================================>] 246,008     39.3K/s   in 6.1s    

2008-11-27 12:31:08 (39.4 KB/s) - `./comic32.exe' saved [246008/246008]

--2008-11-27 12:31:08--  http://mesh.dl.sourceforge.net/sourceforge/corefonts/courie32.exe
Resolving mesh.dl.sourceforge.net... 213.203.218.122
Connecting to mesh.dl.sourceforge.net|213.203.218.122|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://prdownloads.sourceforge.net/corefonts/courie32.exe?download&failedmirror=mesh.dl.sourceforge.net [following]
--2008-11-27 12:31:09--  http://prdownloads.sourceforge.net/corefonts/courie32.exe?download&failedmirror=mesh.dl.sourceforge.net
Resolving prdownloads.sourceforge.net... 216.34.181.60
Connecting to prdownloads.sourceforge.net|216.34.181.60|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://switch.dl.sourceforge.net/sourceforge/corefonts/courie32.exe [following]
--2008-11-27 12:31:10--  http://switch.dl.sourceforge.net/sourceforge/corefonts/courie32.exe
Resolving switch.dl.sourceforge.net... 130.59.138.20
Connecting to switch.dl.sourceforge.net|130.59.138.20|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://prdownloads.sourceforge.net/corefonts/courie32.exe?download&failedmirror=switch.dl.sourceforge.net [following]
--2008-11-27 12:31:11--  http://prdownloads.sourceforge.net/corefonts/courie32.exe?download&failedmirror=switch.dl.sourceforge.net
Connecting to prdownloads.sourceforge.net|216.34.181.60|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://optusnet.dl.sourceforge.net/sourceforge/corefonts/courie32.exe [following]
--2008-11-27 12:31:12--  http://optusnet.dl.sourceforge.net/sourceforge/corefonts/courie32.exe
Resolving optusnet.dl.sourceforge.net... 211.29.132.142
Connecting to optusnet.dl.sourceforge.net|211.29.132.142|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://prdownloads.sourceforge.net/corefonts/courie32.exe?download&failedmirror=optusnet.dl.sourceforge.net [following]
--2008-11-27 12:31:14--  http://prdownloads.sourceforge.net/corefonts/courie32.exe?download&failedmirror=optusnet.dl.sourceforge.net
Connecting to prdownloads.sourceforge.net|216.34.181.60|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://optusnet.dl.sourceforge.net/sourceforge/corefonts/courie32.exe [following]
--2008-11-27 12:31:14--  http://optusnet.dl.sourceforge.net/sourceforge/corefonts/courie32.exe
Connecting to optusnet.dl.sourceforge.net|211.29.132.142|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://prdownloads.sourceforge.net/corefonts/courie32.exe?download&failedmirror=optusnet.dl.sourceforge.net [following]
--2008-11-27 12:31:15--  http://prdownloads.sourceforge.net/corefonts/courie32.exe?download&failedmirror=optusnet.dl.sourceforge.net
Connecting to prdownloads.sourceforge.net|216.34.181.60|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://jaist.dl.sourceforge.net/sourceforge/corefonts/courie32.exe [following]
--2008-11-27 12:31:15--  http://jaist.dl.sourceforge.net/sourceforge/corefonts/courie32.exe
Resolving jaist.dl.sourceforge.net... 150.65.7.130
Connecting to jaist.dl.sourceforge.net|150.65.7.130|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 646368 (631K) [application/octet-stream]
Saving to: `./courie32.exe'

100%[======================================>] 646,368     39.3K/s   in 16s     

2008-11-27 12:31:32 (39.4 KB/s) - `./courie32.exe' saved [646368/646368]

--2008-11-27 12:31:32--  http://mesh.dl.sourceforge.net/sourceforge/corefonts/georgi32.exe
Resolving mesh.dl.sourceforge.net... 213.203.218.122
Connecting to mesh.dl.sourceforge.net|213.203.218.122|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://prdownloads.sourceforge.net/corefonts/georgi32.exe?download&failedmirror=mesh.dl.sourceforge.net [following]
--2008-11-27 12:31:33--  http://prdownloads.sourceforge.net/corefonts/georgi32.exe?download&failedmirror=mesh.dl.sourceforge.net
Resolving prdownloads.sourceforge.net... 216.34.181.60
Connecting to prdownloads.sourceforge.net|216.34.181.60|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://puzzle.dl.sourceforge.net/sourceforge/corefonts/georgi32.exe [following]
--2008-11-27 12:31:34--  http://puzzle.dl.sourceforge.net/sourceforge/corefonts/georgi32.exe
Resolving puzzle.dl.sourceforge.net... 195.141.111.5
Connecting to puzzle.dl.sourceforge.net|195.141.111.5|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 392440 (383K) [application/octet-stream]
Saving to: `./georgi32.exe'

100%[======================================>] 392,440     39.3K/s   in 9.7s    

2008-11-27 12:31:44 (39.4 KB/s) - `./georgi32.exe' saved [392440/392440]

--2008-11-27 12:31:44--  http://mesh.dl.sourceforge.net/sourceforge/corefonts/impact32.exe
Resolving mesh.dl.sourceforge.net... 213.203.218.122
Connecting to mesh.dl.sourceforge.net|213.203.218.122|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://prdownloads.sourceforge.net/corefonts/impact32.exe?download&failedmirror=mesh.dl.sourceforge.net [following]
--2008-11-27 12:31:45--  http://prdownloads.sourceforge.net/corefonts/impact32.exe?download&failedmirror=mesh.dl.sourceforge.net
Resolving prdownloads.sourceforge.net... 216.34.181.60
Connecting to prdownloads.sourceforge.net|216.34.181.60|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://optusnet.dl.sourceforge.net/sourceforge/corefonts/impact32.exe [following]
--2008-11-27 12:31:46--  http://optusnet.dl.sourceforge.net/sourceforge/corefonts/impact32.exe
Resolving optusnet.dl.sourceforge.net... 211.29.132.142
Connecting to optusnet.dl.sourceforge.net|211.29.132.142|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://prdownloads.sourceforge.net/corefonts/impact32.exe?download&failedmirror=optusnet.dl.sourceforge.net [following]
--2008-11-27 12:31:48--  http://prdownloads.sourceforge.net/corefonts/impact32.exe?download&failedmirror=optusnet.dl.sourceforge.net
Connecting to prdownloads.sourceforge.net|216.34.181.60|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://ufpr.dl.sourceforge.net/sourceforge/corefonts/impact32.exe [following]
--2008-11-27 12:31:49--  http://ufpr.dl.sourceforge.net/sourceforge/corefonts/impact32.exe
Resolving ufpr.dl.sourceforge.net... 200.236.31.1, 200.17.202.1
Connecting to ufpr.dl.sourceforge.net|200.236.31.1|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 173288 (169K) [application/x-msdos-program]
Saving to: `./impact32.exe'

100%[======================================>] 173,288     36.8K/s   in 4.5s    

2008-11-27 12:31:57 (37.4 KB/s) - `./impact32.exe' saved [173288/173288]

--2008-11-27 12:31:57--  http://mesh.dl.sourceforge.net/sourceforge/corefonts/times32.exe
Resolving mesh.dl.sourceforge.net... 213.203.218.122
Connecting to mesh.dl.sourceforge.net|213.203.218.122|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://prdownloads.sourceforge.net/corefonts/times32.exe?download&failedmirror=mesh.dl.sourceforge.net [following]
--2008-11-27 12:31:59--  http://prdownloads.sourceforge.net/corefonts/times32.exe?download&failedmirror=mesh.dl.sourceforge.net
Resolving prdownloads.sourceforge.net... 216.34.181.60
Connecting to prdownloads.sourceforge.net|216.34.181.60|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://jaist.dl.sourceforge.net/sourceforge/corefonts/times32.exe [following]
--2008-11-27 12:32:00--  http://jaist.dl.sourceforge.net/sourceforge/corefonts/times32.exe
Resolving jaist.dl.sourceforge.net... 150.65.7.130
Connecting to jaist.dl.sourceforge.net|150.65.7.130|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 661728 (646K) [application/octet-stream]
Saving to: `./times32.exe'

100%[======================================>] 661,728     21.1K/s   in 21s     

2008-11-27 12:32:21 (30.7 KB/s) - `./times32.exe' saved [661728/661728]

--2008-11-27 12:32:21--  http://mesh.dl.sourceforge.net/sourceforge/corefonts/trebuc32.exe
Resolving mesh.dl.sourceforge.net... 213.203.218.122
Connecting to mesh.dl.sourceforge.net|213.203.218.122|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://prdownloads.sourceforge.net/corefonts/trebuc32.exe?download&failedmirror=mesh.dl.sourceforge.net [following]
--2008-11-27 12:32:22--  http://prdownloads.sourceforge.net/corefonts/trebuc32.exe?download&failedmirror=mesh.dl.sourceforge.net
Resolving prdownloads.sourceforge.net... 216.34.181.60
Connecting to prdownloads.sourceforge.net|216.34.181.60|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://optusnet.dl.sourceforge.net/sourceforge/corefonts/trebuc32.exe [following]
--2008-11-27 12:32:23--  http://optusnet.dl.sourceforge.net/sourceforge/corefonts/trebuc32.exe
Resolving optusnet.dl.sourceforge.net... 211.29.132.142
Connecting to optusnet.dl.sourceforge.net|211.29.132.142|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://prdownloads.sourceforge.net/corefonts/trebuc32.exe?download&failedmirror=optusnet.dl.sourceforge.net [following]
--2008-11-27 12:32:25--  http://prdownloads.sourceforge.net/corefonts/trebuc32.exe?download&failedmirror=optusnet.dl.sourceforge.net
Connecting to prdownloads.sourceforge.net|216.34.181.60|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://surfnet.dl.sourceforge.net/sourceforge/corefonts/trebuc32.exe [following]
--2008-11-27 12:32:26--  http://surfnet.dl.sourceforge.net/sourceforge/corefonts/trebuc32.exe
Resolving surfnet.dl.sourceforge.net... 130.59.138.20
Connecting to surfnet.dl.sourceforge.net|130.59.138.20|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://prdownloads.sourceforge.net/corefonts/trebuc32.exe?download&failedmirror=surfnet.dl.sourceforge.net [following]
--2008-11-27 12:32:26--  http://prdownloads.sourceforge.net/corefonts/trebuc32.exe?download&failedmirror=surfnet.dl.sourceforge.net
Connecting to prdownloads.sourceforge.net|216.34.181.60|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://mesh.dl.sourceforge.net/sourceforge/corefonts/trebuc32.exe [following]
--2008-11-27 12:32:27--  http://mesh.dl.sourceforge.net/sourceforge/corefonts/trebuc32.exe
Connecting to mesh.dl.sourceforge.net|213.203.218.122|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://prdownloads.sourceforge.net/corefonts/trebuc32.exe?download&failedmirror=mesh.dl.sourceforge.net [following]
--2008-11-27 12:32:28--  http://prdownloads.sourceforge.net/corefonts/trebuc32.exe?download&failedmirror=mesh.dl.sourceforge.net
Reusing existing connection to prdownloads.sourceforge.net:80.
HTTP request sent, awaiting response... 302 Found
Location: http://heanet.dl.sourceforge.net/sourceforge/corefonts/trebuc32.exe [following]
--2008-11-27 12:32:29--  http://heanet.dl.sourceforge.net/sourceforge/corefonts/trebuc32.exe
Resolving heanet.dl.sourceforge.net... 193.1.193.66
Connecting to heanet.dl.sourceforge.net|193.1.193.66|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 357200 (349K) [application/octet-stream]
Saving to: `./trebuc32.exe'

100%[======================================>] 357,200     39.3K/s   in 8.9s    

2008-11-27 12:32:38 (39.4 KB/s) - `./trebuc32.exe' saved [357200/357200]

--2008-11-27 12:32:38--  http://mesh.dl.sourceforge.net/sourceforge/corefonts/verdan32.exe
Resolving mesh.dl.sourceforge.net... 213.203.218.122
Connecting to mesh.dl.sourceforge.net|213.203.218.122|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://prdownloads.sourceforge.net/corefonts/verdan32.exe?download&failedmirror=mesh.dl.sourceforge.net [following]
--2008-11-27 12:32:39--  http://prdownloads.sourceforge.net/corefonts/verdan32.exe?download&failedmirror=mesh.dl.sourceforge.net
Resolving prdownloads.sourceforge.net... 216.34.181.60
Connecting to prdownloads.sourceforge.net|216.34.181.60|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://optusnet.dl.sourceforge.net/sourceforge/corefonts/verdan32.exe [following]
--2008-11-27 12:32:40--  http://optusnet.dl.sourceforge.net/sourceforge/corefonts/verdan32.exe
Resolving optusnet.dl.sourceforge.net... 211.29.132.142
Connecting to optusnet.dl.sourceforge.net|211.29.132.142|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://prdownloads.sourceforge.net/corefonts/verdan32.exe?download&failedmirror=optusnet.dl.sourceforge.net [following]
--2008-11-27 12:32:41--  http://prdownloads.sourceforge.net/corefonts/verdan32.exe?download&failedmirror=optusnet.dl.sourceforge.net
Connecting to prdownloads.sourceforge.net|216.34.181.60|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://switch.dl.sourceforge.net/sourceforge/corefonts/verdan32.exe [following]
--2008-11-27 12:32:42--  http://switch.dl.sourceforge.net/sourceforge/corefonts/verdan32.exe
Resolving switch.dl.sourceforge.net... 130.59.138.20
Connecting to switch.dl.sourceforge.net|130.59.138.20|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://prdownloads.sourceforge.net/corefonts/verdan32.exe?download&failedmirror=switch.dl.sourceforge.net [following]
--2008-11-27 12:32:42--  http://prdownloads.sourceforge.net/corefonts/verdan32.exe?download&failedmirror=switch.dl.sourceforge.net
Connecting to prdownloads.sourceforge.net|216.34.181.60|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://easynews.dl.sourceforge.net/sourceforge/corefonts/verdan32.exe [following]
--2008-11-27 12:32:43--  http://easynews.dl.sourceforge.net/sourceforge/corefonts/verdan32.exe
Resolving easynews.dl.sourceforge.net... 69.16.168.245
Connecting to easynews.dl.sourceforge.net|69.16.168.245|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 351992 (344K) [application/octet-stream]
Saving to: `./verdan32.exe'

100%[======================================>] 351,992     39.3K/s   in 8.7s    

2008-11-27 12:32:52 (39.4 KB/s) - `./verdan32.exe' saved [351992/351992]

--2008-11-27 12:32:52--  http://mesh.dl.sourceforge.net/sourceforge/corefonts/webdin32.exe
Resolving mesh.dl.sourceforge.net... 213.203.218.122
Connecting to mesh.dl.sourceforge.net|213.203.218.122|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://prdownloads.sourceforge.net/corefonts/webdin32.exe?download&failedmirror=mesh.dl.sourceforge.net [following]
--2008-11-27 12:32:53--  http://prdownloads.sourceforge.net/corefonts/webdin32.exe?download&failedmirror=mesh.dl.sourceforge.net
Resolving prdownloads.sourceforge.net... 216.34.181.60
Connecting to prdownloads.sourceforge.net|216.34.181.60|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://kent.dl.sourceforge.net/sourceforge/corefonts/webdin32.exe [following]
--2008-11-27 12:32:53--  http://kent.dl.sourceforge.net/sourceforge/corefonts/webdin32.exe
Resolving kent.dl.sourceforge.net... 212.219.56.167
Connecting to kent.dl.sourceforge.net|212.219.56.167|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 185072 (181K) [application/octet-stream]
Saving to: `./webdin32.exe'

100%[======================================>] 185,072     24.4K/s   in 7.7s    

2008-11-27 12:33:02 (23.5 KB/s) - `./webdin32.exe' saved [185072/185072]

Extracting cabinet: andale32.exe
  extracting fontinst.inf
  extracting andale.inf
  extracting fontinst.exe
  extracting AndaleMo.TTF
  extracting ADVPACK.DLL
  extracting W95INF32.DLL
  extracting W95INF16.DLL

All done, no errors.
Extracting cabinet: arialb32.exe
  extracting fontinst.exe
  extracting fontinst.inf
  extracting AriBlk.TTF

All done, no errors.
Extracting cabinet: arial32.exe
  extracting FONTINST.EXE
  extracting fontinst.inf
  extracting Ariali.TTF
  extracting Arialbd.TTF
  extracting Arialbi.TTF
  extracting Arial.TTF

All done, no errors.
Extracting cabinet: comic32.exe
  extracting fontinst.inf
  extracting Comicbd.TTF
  extracting Comic.TTF
  extracting fontinst.exe

All done, no errors.
Extracting cabinet: courie32.exe
  extracting cour.ttf
  extracting courbd.ttf
  extracting courbi.ttf
  extracting fontinst.inf
  extracting couri.ttf
  extracting fontinst.exe

All done, no errors.
Extracting cabinet: georgi32.exe
  extracting fontinst.inf
  extracting Georgiaz.TTF
  extracting Georgiab.TTF
  extracting Georgiai.TTF
  extracting Georgia.TTF
  extracting fontinst.exe

All done, no errors.
Extracting cabinet: impact32.exe
  extracting fontinst.exe
  extracting Impact.TTF
  extracting fontinst.inf

All done, no errors.
Extracting cabinet: times32.exe
  extracting fontinst.inf
  extracting Times.TTF
  extracting Timesbd.TTF
  extracting Timesbi.TTF
  extracting Timesi.TTF
  extracting FONTINST.EXE

All done, no errors.
Extracting cabinet: trebuc32.exe
  extracting FONTINST.EXE
  extracting trebuc.ttf
  extracting Trebucbd.ttf
  extracting trebucbi.ttf
  extracting trebucit.ttf
  extracting fontinst.inf

All done, no errors.
Extracting cabinet: verdan32.exe
  extracting fontinst.exe
  extracting fontinst.inf
  extracting Verdanab.TTF
  extracting Verdanai.TTF
  extracting Verdanaz.TTF
  extracting Verdana.TTF

All done, no errors.
Extracting cabinet: webdin32.exe
  extracting fontinst.exe
  extracting Webdings.TTF
  extracting fontinst.inf
  extracting Licen.TXT

All done, no errors.
All fonts downloaded and installed.
Updating fontconfig cache for /usr/share/fonts/truetype/msttcorefonts
No CIDSupplement specified for Batang-Bold, defaulting to 0.
No CIDSupplement specified for UMingCN, defaulting to 0.
No CIDSupplement specified for KochiGothic-Regular-JaH, defaulting to 0.
No CIDSupplement specified for KochiGothic-Regular, defaulting to 0.
No CIDSupplement specified for KochiMincho-Regular-JaH, defaulting to 0.
No CIDSupplement specified for Batang-Regular, defaulting to 0.
No CIDSupplement specified for Dotum-Bold, defaulting to 0.
No CIDSupplement specified for KochiMincho-Regular, defaulting to 0.
No CIDSupplement specified for Dotum-Regular, defaulting to 0.

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
adriaan@adriaan-desktop:~$ 

```

---

### Post by Bödvar on 2008-11-27
So, after it was done, I can install my .deb package now.

But what is this and why did it happen? Is it worth mentioning that my computer just turned itself off and immediately on again three times today while I was browsing the web, listening to music or not doing anything particular at all (lying on my bed studying, computer just goes off???)

Thanks for any help and information.

---

### Post by Elfy on 2008-11-27
> dpkg was interruptedThat is why it happened - while you were installing msttcorefonts - maybe as part of ubuntu-restricted-extras - it got stopped from completing. Could possibly be that the pc crashed - or you didn't notice the java EULA behind - it happened to me once.

So it is necessary for the packages which were half installed to be fully installed - that is why you got the error message and the command you needed to run to fix it.

---

### Post by Bödvar on 2008-11-27
Okay thanks. I just wanted to understand. Thanks.

---

### Post by Elfy on 2008-11-27
welcome - can you mark thread solved please :)

---

### Post by Bödvar on 2008-11-27
Sure.

---

