---
title: "open ports/ major security issue"
date: 2005-11-14
forum: General Help
---

### Post by ivago on 2005-11-14
Hi,

I just portscanned my localhost and found that there are an incredible amount of services are running in the background... daemons like finger and such wich I've never started myself in the first place.

When I go to the administration --> services in GNOME I only see a couple of services like klogd, ssh and samba but nothing else like the once below.

How can I make sure that these services don't get started autmatically?

Now I tried shutting down as much as possible via /etc/init.d/$daemon stop :( 

all by all a serious securtiy issue if this is the default install services :roll:

```

gb@TACO:/etc/init.d$ nmap -P0 localhost

Starting nmap 3.81 ( http://www.insecure.org/nmap/ ) at 2005-11-14 12:09 CET
Interesting ports on localhost.localdomain (127.0.0.1):
(The 1636 ports scanned but not shown below are in state: closed)
PORT      STATE SERVICE
1/tcp     open  tcpmux
11/tcp    open  systat
15/tcp    open  netstat
22/tcp    open  ssh
79/tcp    open  finger
111/tcp   open  rpcbind
119/tcp   open  nntp
139/tcp   open  netbios-ssn
143/tcp   open  imap
445/tcp   open  microsoft-ds
540/tcp   open  uucp
631/tcp   open  ipp
635/tcp   open  unknown
1080/tcp  open  socks
1524/tcp  open  ingreslock
2000/tcp  open  callbook
6667/tcp  open  irc
12345/tcp open  NetBus
12346/tcp open  NetBus
27665/tcp open  Trinoo_Master
31337/tcp open  Elite
32770/tcp open  sometimes-rpc3
32771/tcp open  sometimes-rpc5
32772/tcp open  sometimes-rpc7
32773/tcp open  sometimes-rpc9
32774/tcp open  sometimes-rpc11
54320/tcp open  bo2k

Nmap finished: 1 IP address (1 host up) scanned in 0.063 seconds
gb@TACO:/etc/init.d$

```

---

### Post by nagilum on 2005-11-14
Since you scanned localhost it does not mean that these ports are also open on your public interface(s). It's impossible to reach the localhost interface from another computer so not neccessarily a security issue. A scan on your public interfaces (like eth0) will tell you what is open to others.
Nonetheless there are quite some services open. What does 'netstat -lptnu' tell you? Does it see the same open ports? You can also identify the processes on the netstat output which might help in disabling the services.

---

### Post by ivago on 2005-11-14
when I do a scan on my eth0 I still get the same output, strange thing is that I see stuff like the obsolete trojans like netbus or b02k (wich was windows only?).

As far as I know I  only enabled samba and ssh on this box but I did install portsentry wich might explain this strange behaviour. Altough stuff like finger is definetely running cause I get feedback from 'finger gb'

Security is on my site not a real issue because I'm firewalled through my router but I wonder how people who are connected with a direct connection to the internet survive this.

Solution is to install firestarter or run iptables but it's still a big chunck of ressources getting wasted with a setup like this.

```

gb@TACO:~$ netstat -lptnu
(Not all processes could be identified, non-owned process info
 will not be shown, you would have to be root to see it all.)
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name 
tcp        0      0 0.0.0.0:1               0.0.0.0:*               LISTEN     - 
tcp        0      0 127.0.0.1:32769         0.0.0.0:*               LISTEN     - 
tcp        0      0 0.0.0.0:20034           0.0.0.0:*               LISTEN     - 
tcp        0      0 127.0.0.1:32770         0.0.0.0:*               LISTEN     - 
tcp        0      0 0.0.0.0:32771           0.0.0.0:*               LISTEN     - 
tcp        0      0 0.0.0.0:32772           0.0.0.0:*               LISTEN     - 
tcp        0      0 0.0.0.0:40421           0.0.0.0:*               LISTEN     - 
tcp        0      0 0.0.0.0:32773           0.0.0.0:*               LISTEN     - 
tcp        0      0 0.0.0.0:32774           0.0.0.0:*               LISTEN     - 
tcp        0      0 0.0.0.0:31337           0.0.0.0:*               LISTEN     - 
tcp        0      0 0.0.0.0:6667            0.0.0.0:*               LISTEN     - 
tcp        0      0 0.0.0.0:11              0.0.0.0:*               LISTEN     - 
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN     - 
tcp        0      0 0.0.0.0:5742            0.0.0.0:*               LISTEN     - 
tcp        0      0 0.0.0.0:143             0.0.0.0:*               LISTEN     - 
tcp        0      0 0.0.0.0:111             0.0.0.0:*               LISTEN     - 
tcp        0      0 0.0.0.0:79              0.0.0.0:*               LISTEN     - 
tcp        0      0 0.0.0.0:15              0.0.0.0:*               LISTEN     - 
tcp        0      0 0.0.0.0:54320           0.0.0.0:*               LISTEN     - 
tcp        0      0 0.0.0.0:2000            0.0.0.0:*               LISTEN     - 
tcp        0      0 0.0.0.0:27665           0.0.0.0:*               LISTEN     - 
tcp        0      0 0.0.0.0:1524            0.0.0.0:*               LISTEN     - 
tcp        0      0 0.0.0.0:119             0.0.0.0:*               LISTEN     - 
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     - 
tcp        0      0 0.0.0.0:1080            0.0.0.0:*               LISTEN     - 
tcp        0      0 0.0.0.0:12345           0.0.0.0:*               LISTEN     - 
tcp        0      0 0.0.0.0:12346           0.0.0.0:*               LISTEN     - 
tcp        0      0 0.0.0.0:635             0.0.0.0:*               LISTEN     - 
tcp        0      0 0.0.0.0:49724           0.0.0.0:*               LISTEN     - 
tcp        0      0 0.0.0.0:540             0.0.0.0:*               LISTEN     - 
tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN     - 
tcp6       0      0 :::22                   :::*                    LISTEN     - 
udp        0      0 0.0.0.0:640             0.0.0.0:*                          - 
udp        0      0 0.0.0.0:641             0.0.0.0:*                          - 
udp        0      0 0.0.0.0:513             0.0.0.0:*                          - 
udp        0      0 0.0.0.0:1               0.0.0.0:*                          - 
udp        0      0 0.0.0.0:32770           0.0.0.0:*                          - 
udp        0      0 0.0.0.0:32771           0.0.0.0:*                          - 
udp        0      0 0.0.0.0:32772           0.0.0.0:*                          - 
udp        0      0 0.0.0.0:32773           0.0.0.0:*                          - 


```


```

gb@TACO:~$ nmap -P0 192.168.1.2

Starting nmap 3.81 ( http://www.insecure.org/nmap/ ) at 2005-11-14 16:48 CET
Interesting ports on TACO (192.168.1.2):
(The 1638 ports scanned but not shown below are in state: closed)
PORT      STATE SERVICE
1/tcp     open  tcpmux
11/tcp    open  systat
15/tcp    open  netstat
22/tcp    open  ssh
79/tcp    open  finger
111/tcp   open  rpcbind
119/tcp   open  nntp
139/tcp   open  netbios-ssn
143/tcp   open  imap
445/tcp   open  microsoft-ds
540/tcp   open  uucp
635/tcp   open  unknown
1080/tcp  open  socks
1524/tcp  open  ingreslock
2000/tcp  open  callbook
6667/tcp  open  irc
12345/tcp open  NetBus
12346/tcp open  NetBus
27665/tcp open  Trinoo_Master
31337/tcp open  Elite
32771/tcp open  sometimes-rpc5
32772/tcp open  sometimes-rpc7
32773/tcp open  sometimes-rpc9
32774/tcp open  sometimes-rpc11
54320/tcp open  bo2k

Nmap finished: 1 IP address (1 host up) scanned in 0.073 seconds
gb@TACO:~$

```

---

### Post by ivago on 2005-11-14
it seems portsentry was playing tricks with me (wich was not a bug but a feature :wink: )
nevertheless I can still finger myself (pardon my french), is this normal on ubuntu because a finger-servers seems to be quite oldskool nowadays :?:
There's also no finger daemon in /etc/init.d 

```

gb@TACO:~$sudo apt-get remove portsentry
<snip>
Stopping anti portscan daemon: portsentry.
gb@TACO:~$ nmap -P0 192.168.1.2

Starting nmap 3.81 ( http://www.insecure.org/nmap/ ) at 2005-11-14 17:02 CET
Interesting ports on TACO (192.168.1.2):
(The 1660 ports scanned but not shown below are in state: closed)
PORT    STATE SERVICE
22/tcp  open  ssh
139/tcp open  netbios-ssn
445/tcp open  microsoft-ds

Nmap finished: 1 IP address (1 host up) scanned in 0.073 seconds
gb@TACO:~$ finger gb
Login: gb                               Name: Geert Batsleer
Directory: /home/gb                     Shell: /bin/bash
On since Mon Nov 14 16:40 (CET) on :0 (messages off)
On since Mon Nov 14 16:40 (CET) on pts/0 from :0.0
No mail.
No Plan.
gb@TACO:~$

```

---

### Post by nagilum on 2005-11-14
Ah, portsentry.  Never used it but I thought its purpose was to close down a machine not open more ports. Well... "nice" feature. ;)
As for the finger-thing, this is normal. If you run finger on some account on your local machine it reads the information from various files directly without contacting a server.

---

### Post by xurizaemon on 2006-08-03
portsentry's aim is to *look* interesting and open, but at the same time drop replies to hosts that try to touch you in inappropriate places

perhaps "a little knowledge is a bad thing" here: a partially-configured portsentry would make a machine appear very open and tempting, and yet might not correctly block scans from the attacking host

however it's likely that ivago's machine is correctly configured, and the only reason portsentry didn't block him quick smart was because he was scanning from an IP already listed (by autoconfiguration) in /etc/portsentry/portsentry.ignore

had ivago scanned himself from a host which was not already listed there, i suspect he would have found the machine "dropped off the internet" once touched ...

ivago could you let us know what happens if you scan this host from a *remote* machine?

portsentry is good, i think, it blocks a lot of nasties who try to come calling ;)

---

