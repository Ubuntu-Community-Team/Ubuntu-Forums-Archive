---
title: "Can't Ping"
date: 2005-11-12
forum: General Help
---

### Post by Stormspace on 2005-11-12
I cannot ping anything on my network by name. I can browse the network in places, connect to the internet, but cannot ping any network devices on my LAN. Any Ideas?

---

### Post by Eleaf on 2005-11-12
You cannot ping anything on your network by name?  What do you mean?  In what form are you doing the command?

---

### Post by codejunkie on 2005-11-12
[quote=Stormspace]I cannot ping anything on my network by name. I can browse the network in places, connect to the internet, but cannot ping any network devices on my LAN. Any Ideas?[/quote] id could be the way you used the ping command in ubuntu ping has to be launched as root for example: ```
sudo ping 192.168.0.1
``` if you use ping as a normal user it does nothing hope this helps.
edit: never mind i just tried it as a normal user under breezy and it worked fine. i had to always launch it as root under warty, hum or maybe im loosing more than my hair in my old age.

---

### Post by kelsey23 on 2005-11-12
[QUOTE=Stormspace]I cannot ping anything on my network by name. I can browse the network in places, connect to the internet, but cannot ping any network devices on my LAN. Any Ideas?[/QUOTE]
You don't ping by name. You ping by IP adress :-). And you don't have to be logged in as root, either.

---

### Post by Eleaf on 2005-11-12
Yea.  I was wondering in what form you were doing it.  So to ping another computer that has a specific ip address, you would do "ping 192.168.0.3" or something like that.  However doing "ping computername" will not work.  = P

---

### Post by Stormspace on 2005-11-12
This is what I get

```

mccallj@ubuntu:~$ sudo ping tivoserver
Password:
ping: unknown host tivoserver
mccallj@ubuntu:~$

```

I can however ping by IP.

---

### Post by dbott67 on 2005-11-12
[QUOTE=kelsey23]You don't ping by name. You ping by IP adress :-). And you don't have to be logged in as root, either.[/QUOTE]

Well, not to be nitpicky or anything, but you can ping by IP address (ping 192.168.1.100), fully qualified domain name (ping [www.google.com](www.google.com)) or hostname (i.e. ping breezy):
```
dbott@breezy:~$ ping 192.168.1.100
PING 192.168.1.100 (192.168.1.100) 56(84) bytes of data.
64 bytes from 192.168.1.100: icmp_seq=1 ttl=64 time=0.131 ms
64 bytes from 192.168.1.100: icmp_seq=2 ttl=64 time=0.108 ms
64 bytes from 192.168.1.100: icmp_seq=3 ttl=64 time=0.111 ms
64 bytes from 192.168.1.100: icmp_seq=4 ttl=64 time=0.103 ms

[6]+  Stopped                 ping 192.168.1.100
dbott@breezy:~$ ping www.google.com
PING www.l.google.com (64.233.167.99) 56(84) bytes of data.
64 bytes from 64.233.167.99: icmp_seq=1 ttl=244 time=32.8 ms
64 bytes from 64.233.167.99: icmp_seq=2 ttl=244 time=32.4 ms
64 bytes from 64.233.167.99: icmp_seq=3 ttl=244 time=32.9 ms

[7]+  Stopped                 ping www.google.com
dbott@breezy:~$ ping breezy
PING localhost.localdomain (127.0.0.1) 56(84) bytes of data.
64 bytes from localhost.localdomain (127.0.0.1): icmp_seq=1 ttl=64 time=0.117 ms
64 bytes from localhost.localdomain (127.0.0.1): icmp_seq=2 ttl=64 time=0.110 ms
64 bytes from localhost.localdomain (127.0.0.1): icmp_seq=3 ttl=64 time=0.107 ms

[8]+  Stopped                 ping breezy
dbott@breezy:~$
```

To ping a hostname (i.e. the name of the *nix or Windows box, you need to specify the **hostname and IP address** in a special file (I think it's **/etc/hosts** in Linux; 'lmhosts' in Windows) on each computer or setup a DNS server or (in the old Windows world) a WINS server.

-Dave

---

### Post by Stormspace on 2005-11-12
So..netbios through DHCP doesn't work? I mean I can create a hosts file, no prob, but the IP's would change when the lease ran out on the DHCP.

---

### Post by dbott67 on 2005-11-12
[QUOTE=Stormspace]So..netbios through DHCP doesn't work? I mean I can create a hosts file, no prob, but the IP's would change when the lease ran out on the DHCP.[/QUOTE]

That's right.... NetBIOS is basically a legacy from the old MS LAN Manager days.  On Windows computers, you could enable NBT over TCP/IP to be backwards-compatible with LANman.

You *could* setup an DNS server internally and then your hostnames will be mapped for you -or- you could use 'static' DHCP.  Many DHCP servers will allow you to assign the IP address to a specific MAC address, which prevents the IP address from being assigned to another computer.  This is what I use on my home network (D-Link router) to keep the same IP for each host.  If you do it this way, the 'hosts' file would never change.

-Dave

---

### Post by Stormspace on 2005-11-12
Well.... can the dns server and the DHCP server run on different devices?

---

### Post by Zwack on 2005-11-13
[QUOTE=Stormspace]Well.... can the dns server and the DHCP server run on different devices?[/QUOTE]

Yes... Or you could run them on the same device... They are essentially unrelated...

Z.

---

### Post by Stormspace on 2005-11-14
I'm using a router for my DHCP server, but I do have a CENTOS fileserver that I could configure as a DNS server. Will I still need a hosts table, or will it build dynamically as PC's join the LAN? Also, would a WINS server allow Linux boxes to ping and browse by name?

---

### Post by dbott67 on 2005-11-14
In a nutshell, WINS is for Windows only (it's a legacy from the old NT3.51 and 4.0 days) that allowed the NETBIOS name (aka the computername) to be registered on  larger networks.

On small Win9x P2P networks, the first computer would elect itself as the 'browse master' on register all new Windows computers on the network so that you could use 'Network Neighbourhood' to browse for other computers easily, but this was really only useful on smaller networks of less than 15 computers or so.

On larger MS networks, you would need to setup a WINS server to register all (Windows) computers dynamically as they logged on.  Today, MS has essentially dropped WINS in favour of DNS, except for where required for legacy reasons:

[QUOTE=From ComputerPerformance.co.uk]
[http://www.computerperformance.co.uk/w2k3/services/WINS_Home.htm](http://www.computerperformance.co.uk/w2k3/services/WINS_Home.htm)
The first point to remember about WINS is that only Microsoft clients use WINS servers for name resolution, whereas Linux, Unix and everyone else on the internet, use DNS exclusively.  To keep matters in perspective, Active Directory, Exchange and IIS also require DNS.  95% of the time modern Microsoft products prefer DNS, but just occasionally they need to find a NetBIOS resource name - come in WINS.  The 'killer' reason for implementing WINS is that Exchange, even Exchange 2003, needs NetBIOS name resolution.
...While both WINS and DNS deal with mapping ComputerName to IP addresses, there are two important differences; DNS is hierarchical and can support up to 254 characters, WINS, on the other hand, is a flat-field database limited to 15 letters.  One of the few advantages that WINS formerly had over DNS was that WINS is dynamic.  Well, starting with Windows 2000, DNS is also dynamic, so the only point of WINS in the 21st century is specifically for NetBIOS name resolution.

Keep in mind, especially when troubleshooting, the reason why we need databases such as WINS or DNS. The answer is name resolution.  We humans prefer to remember friendly names like BigServer, whereas computers prefer IP addresses in dot decimal notation for example, 192.168.0.23.

Name resolution started with two files called 'hosts' and LMHosts files.  The hosts file evolved into DNS and WINS took over the name resolution provided by LMHosts.  Every Microsoft machine is born with these files in the folder: %systemroot%\system32\drivers\etc\. Here is a typical entry for LMHosts.

10.54.94.13   bigserver[/QUOTE]

So, in your case, you'll need to setup a DNS server or use static IPs and the 'hosts' file (linux) and 'lmhosts' for Windows.

-Dave

---

### Post by avc on 2005-11-23
You can ping Windows computers from Ubuntu if you "sudo apt-get install winbind" and change one line in /etc/nsswitch.conf from:
```
hosts:	files dns
```
to
```
hosts:	files dns wins
```

Got it from here [http://www.ubuntuforums.org/showthread.php?t=88206&highlight=netbios+ping](http://www.ubuntuforums.org/showthread.php?t=88206&highlight=netbios+ping) Thanks javiwwweb!

[edit]
Fixed a typo: "host" should be "hosts". Thanks to Stormspace for catching this.
[/edit]

---

### Post by Stormspace on 2005-12-09
[QUOTE=avc]You can ping Windows computers from Ubuntu if you "sudo apt-get install winbind" and change one line in /etc/nsswitch.conf from:
```
host: files dns
```
to
```
host: files dns wins
```

Got it from here [http://www.ubuntuforums.org/showthread.php?t=88206&highlight=netbios+ping](http://www.ubuntuforums.org/showthread.php?t=88206&highlight=netbios+ping) Thanks javiwwweb![/QUOTE]

Just to help anyone that happens along this thread. The above post is incorrect. If you follow these instructions you will hose your machine. However I believe the error is merely a typo and not a reflection of avc's Linux savvy. His solution did work eventually, just make certain the code looks like this.

```
hosts: 		files dns wins
```

---

