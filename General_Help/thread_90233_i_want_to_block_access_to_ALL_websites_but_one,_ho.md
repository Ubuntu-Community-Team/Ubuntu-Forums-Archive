---
title: "i want to block access to ALL websites but one, how?"
date: 2005-11-14
forum: General Help
---

### Post by herot on 2005-11-14
my company wants me to set up a computer that only has access to my company's web site... and blocks any and all attempts to access any other websites... is there a way whitelist version of the hosts file??? can i do this with the hosts file? can i whitelist actual sites in firefox???

any help or advice would be appreciated...

---

### Post by Original Brownster on 2005-11-14
You could look at modifying your firewall rules to achieve this, effectively blocking all outbound connections on port 80 except for the one you want.
I had a quick look at 'firestarter' which I use and you can write something like that real easy I think.

---

### Post by herot on 2005-11-14
any idea what specifically i would write ???

---

### Post by poptones on 2005-11-14
If it's for a kiosk you could just go to the network panel, click the dns tab and make the only entry "127.0.0.1." Then the machine will only be able to find other machines listed in the HOSTS file. People could still enter numeric IPs, but you'll have no name resolution outside your hosts "whitelist."

---

### Post by herot on 2005-11-14
ok, so i make localhost the only dns machine and then go into my hosts file and put in the website i want them to have access to?

sounds simple enough...

thanks!

and yes... its basically just a kiosk. will need to be able to access a share on a 2003 server tho, will this interfere?

---

### Post by N6546R on 2005-11-14
How about modifying the routing table? Let's say the site you want to allow access to is 192.168.2.3, and your router is sitting at 212.4.4.6. The routing table could look like:

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.3    212.4.4.6         255.255.255.0   UH     0      0        0 eth0

You'd have no default route, so requests to random IPs wouldn't go anywhere. You'd also want entries in /etc/hosts to point to whatever hostname the links on the web page point to, and routes for each of them if they don't all exist on the same server.

Perry

---

### Post by herot on 2005-11-14
thanks! i made the website so i know that all the links are on the same server...
so i would just put [www.mycompany.com](www.mycompany.com) in the host files after modifying the route table??

---

### Post by xlyz on 2005-11-14
set the browser to use a non existing proxy. put the allowed sites in the exception field

---

### Post by herot on 2005-11-14
[QUOTE=xlyz]set the browser to use a non existing proxy. put the allowed sites in the exception field[/QUOTE]
i have done this on windows machines and i dont really like this method at all. thanks for the input tho!

---

### Post by poptones on 2005-11-14
You will need a proper host entry of course... the domain AND the proper IP address you are connecting to.

for your local database server, same thing - just give it a name and an IP address in hosts.

---

### Post by slux on 2005-11-14
routing is an interesting approach but maybe not really a very clean solution and has some issues. Killing the dns only prevents resolving hostnames so anyone so inclined can still get thru with ip-addresses. Letting netfilter block outgoing connections to undesired sites is really the best local solution although if this is just the browser we are talking about, it can also be done just for the browser (with mozilla at least).

The most foolproof way is of course to arrange for the filtering on a router or the proxy if you are accessing the net thru one.

---

### Post by herot on 2005-11-14
is netfilter a firewall like firestarter???

---

### Post by herot on 2005-11-14
ok i figured out how to do it using firestarter(its really easy).  i will incorporate this method on the kiosk computer and then deny access to the firewall controls for the kiosk user... anybody see any problems with this solution??

the ppl using this kiosk will be employees who i KNOW do not have the required knowledge (or desire) to figure out how to gain root, or attempt to foil the firewall in  some other way either(not that it would be too terribly big a deal if they did anyway...).

---

### Post by Ride Jib on 2005-11-14
The method of setting up your firewall to block port 80 is not sufficient. Websites also run on ports 8080, and 443, commonly, but are not limited to any specific port. Aside from that you also have to worry about tunneling. 

Aside from that, you'd be surprised what the boredom of sitting at a kiosk can do for one's curiosity and desire to browse the web.

---

### Post by herot on 2005-11-14
no... its not blocking port 80... its a whitelist with only the website i choose listed in it... they cant get to the firewall because they dont have access to the firewall control program... these ppl are 40+ and dont know how to right click in windows... have only ever used windows when doing anything with a computer. AND ubuntu (severly stripped down gui,((cant even access places, or system menu)) and can only access firefox (no terminal either) (disabled Fn ing to new shell window) and all hotkeys destroyed except for ctrl-shift-t-e-r-m-[ (for me to access terminal) ... is what they'll be using.  :)

dont worry,... im not too proud of this tecnological terror ive created...

i think it will suffice

---

### Post by gunny on 2005-11-14
The fastest way would be to use your firewall (firestarter) and set policy to restrictive for all outbound traffic then add rule to allow access to [www.mycompany.com](www.mycompany.com) done. end of story.

Be yourself, who else is better qualified!
gunny :cool:

---

### Post by uberlinux on 2005-11-15
Hello,
Basically, I would not use something as easy and obvious as firestarter, or any GUI firewall tool.  You should use iptables directly from the command line to block everything except for traffic to [www.company.com](www.company.com).  I have provided a sample of what the iptables -L command should print when this has been done successfully.
I would then restrict access to the iptables command for everyone that needs sudo access.  This will not be easily defeated, as you must then be logged in as root in order to modify iptables.
If I were you, I would read up on iptables as it is one of the most important things you will use as an administrator.




```


Chain INBOUND (1 references)
target     prot opt source               destination
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTAB
LISHED
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTAB
LISHED
LSI        all  --  anywhere             anywhere

Chain INPUT (policy DROP)
target     prot opt source               destination
ACCEPT     tcp  --  192.168.0.1          anywhere            tcp flags:!SYN,RST,
ACK/SYN
ACCEPT     udp  --  192.168.0.1          anywhere
ACCEPT     all  --  anywhere             anywhere
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec b
urst 5
DROP       all  --  anywhere             255.255.255.255
DROP       all  --  anywhere             192.168.0.255
DROP       all  --  BASE-ADDRESS.MCAST.NET/8  anywhere
DROP       all  --  anywhere             BASE-ADDRESS.MCAST.NET/8
DROP       all  --  255.255.255.255      anywhere
DROP       all  --  anywhere             0.0.0.0
DROP       all  --  anywhere             anywhere            state INVALID
LSI        all  -f  anywhere             anywhere            limit: avg 10/min b
urst 5
INBOUND    all  --  anywhere             anywhere
LOG_FILTER  all  --  anywhere             anywhere
LOG        all  --  anywhere             anywhere            LOG level info pref
ix `Unknown Input'

Chain FORWARD (policy DROP)
target     prot opt source               destination
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec b
urst 5
LOG_FILTER  all  --  anywhere             anywhere
LOG        all  --  anywhere             anywhere            LOG level info pref
ix `Unknown Forward'

Chain LOG_FILTER (5 references)
target     prot opt source               destination

Chain LSI (2 references)
target     prot opt source               destination
LOG_FILTER  all  --  anywhere             anywhere
LOG        tcp  --  anywhere             anywhere            tcp flags:SYN,RST,A
CK/SYN limit: avg 1/sec burst 5 LOG level info prefix `Inbound '
DROP       tcp  --  anywhere             anywhere            tcp flags:SYN,RST,A
CK/SYN
LOG        tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,R
ST,ACK/RST limit: avg 1/sec burst 5 LOG level info prefix `Inbound '
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,R
ST,ACK/RST
LOG        icmp --  anywhere             anywhere            icmp echo-request l                                                                           imit: avg 1/sec burst 5 LOG level info prefix `Inbound '
DROP       icmp --  anywhere             anywhere            icmp echo-request
LOG        all  --  anywhere             anywhere            limit: avg 5/sec bu                                                                           rst 5 LOG level info prefix `Inbound '
DROP       all  --  anywhere             anywhere

Chain LSO (1 references)
target     prot opt source               destination
LOG_FILTER  all  --  anywhere             anywhere
LOG        all  --  anywhere             anywhere            limit: avg 5/sec bu                                                                           rst 5 LOG level info prefix `Outbound '
REJECT     all  --  anywhere             anywhere            reject-with icmp-po                                                                           rt-unreachable

Chain OUTBOUND (1 references)
target     prot opt source               destination
ACCEPT     icmp --  anywhere             anywhere
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTAB                                                                           LISHED
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTAB                                                                           LISHED
ACCEPT     all  --  anywhere             gentoo.ubuntu.com
LSO        all  --  anywhere             anywhere

Chain OUTPUT (policy DROP)
target     prot opt source               destination
ACCEPT     tcp  --  192.168.0.101        192.168.0.1         tcp dpt:domain
ACCEPT     udp  --  192.168.0.101        192.168.0.1         udp dpt:domain
ACCEPT     all  --  anywhere             anywhere
DROP       all  --  BASE-ADDRESS.MCAST.NET/8  anywhere
DROP       all  --  anywhere             BASE-ADDRESS.MCAST.NET/8
DROP       all  --  255.255.255.255      anywhere
DROP       all  --  anywhere             0.0.0.0
DROP       all  --  anywhere             anywhere            state INVALID
OUTBOUND   all  --  anywhere             anywhere
LOG_FILTER  all  --  anywhere             anywhere
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Output'

```

---

### Post by pickarooney on 2005-11-15
Just tell the employees not to use outside websites, and fire them if they do? :D

Is the webserver of your company on a local domain or is the site to which access is allowed external?

---

### Post by herot on 2005-11-15
uberlinux, into which part of that code do i put the website i want to allow??

---

### Post by uberlinux on 2005-11-15
[QUOTE=herot]uberlinux, into which part of that code do i put the website i want to allow??[/QUOTE]
Just do a "man iptables"  and it will show you everything.

---

### Post by slux on 2005-11-15
There's not much reason not to use Firestarter unless you anticipate using iptables a lot in the future (and no, not every Linux users needs to know a lot about iptables).

I happen to think the iptables syntax is one of the most horrible aspects of using Linux. *BSD all manage to have a hundred times nicer packet filter syntax.
iptables is just plain ugly.

---

### Post by N6546R on 2005-11-28
[QUOTE=herot]thanks! i made the website so i know that all the links are on the same server...
so i would just put [www.mycompany.com](www.mycompany.com) in the host files after modifying the route table??[/QUOTE]

Yes, that should work.

Perry

---

### Post by mcmuffy on 2005-11-28
This may be a little over the top for your uses but it will definatly do the job.

[http://dansguardian.org/](http://dansguardian.org/)

---

### Post by airtonix on 2007-05-01
yeah i was going to recomend the firestarter whitelist method after reading page 1 of this thread, but you already got to it.

then i remembered that you can do a wildcard thing on 127.0.0.1. but then that would only work for domain names and like someone mentions all the 'free-thinking-company-not-so-drone-like-deviant' has to do is use IP address.

btw i think the host file wildcard thingo was like this : 

> * 127.0.0.1

---

