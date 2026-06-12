---
title: "[SOLVED] Deluge &amp;amp; IPblock"
date: 2008-12-01
forum: General Help
---

### Post by darkcrawler on 2008-12-01
I'm using both Deluge torrent and IPblock (with all lists updated), do i need to configure even the blocklist of Deluge or i'm safe with just IPblock? thanks

---

### Post by uljanow on 2008-12-02
IMHO there's no need to use the blocklist of Deluge if IPblock is installed. For  comparison purposes I wrote a [FAQ entry]("http://iplist.sourceforge.net/faq.html#0x0d").

---

### Post by darkcrawler on 2008-12-02
```
From Iplist FAQ:

Why not use the build-in blocklist feature of my P2P application ?
P2P applications only block connections relevant to their process (transport layer).
However IPblock uses the operating system's firewall interface (network layer) which
has the advantage that all connections regardless of the protocoll, host, process and
content are filtered. Furthermore users of IPblock are in "stealth mode" which
prevents blocked hosts to determine wheter they are online or not. Other features are:
wide range of lists, auto-update, whitelists, multi-threaded design, higly
customizable, ...

```

It seems there's no need to use the Blocklist of Deluge.. But i'm open to other suggestions!

---

### Post by lovinglinux on 2008-12-02
> **darkcrawler said:**
> It seems there's no need to use the Blocklist of Deluge.. But i'm open to other suggestions!

Well, I use Deluge's blocklist plugin and moblock (a network layer ip blocker similar to Iplist) at the same time.

Why?

1 - If the network layer ip blocker fails, then I still have some sort of protection against intruders trying to breach through the p2p application. 

2 - Because the Deluge's plugin does blacklist IPs directly from the the tracker list, so instead of trying to connect to several IPs that will be blocked by the network layer, it only tries to connect to IPs that are whitelisted. I don't really know if this has any impact on reaching high speeds faster, but surely doesn't hurt.

3 - Because I like to use different lists for p2p applications. So I use a less complete list with the system blocker, which allows me to surf the web without much hassle, and a very restrictive additive list for the Deluge's plugin. 

Is up to you to decide if you should use the Deluge's blocklist, but you should really use a network layer ip blocker like Iplist or moblock, because they protect the network and not only the p2p port/protocol/application.

If you decide to use Deluge's blocklist plugin, make sure it is working, because the one provided with the 1.x versions of the application do not work yet. I'm still using Deluge 0.5.x because of this.

BTW, the statement above about the "stealth mode" is not necessarily true. There is a lot of debate about being really stealth, because the firewall needs to drop inbound icmp packages to achieve this. When it does, there is a delay that can be determined by a hacker, suggesting the machine is filtering the packages.

---

### Post by darkcrawler on 2008-12-02
as i wrote in my first post i just use IPblock..
However i never thought of using different lists for Ipblock and for Deluge.. It's suerely a nice idea..
Actually i use Deluge 1.06, but you suggest to use the 0.5.x version?
What list do you use in the Blocklist of Deluge? Thanks

---

### Post by lovinglinux on 2008-12-02
> **darkcrawler said:**
> as i wrote in my first post i just use IPblock.

I know.  :)

> **darkcrawler said:**
> Actually i use Deluge 1.06, but you suggest to use the 0.5.x version?

You should be fine using Deluge 1.06 with iplist. The other things I said before, about using both blocking systems, are just a matter of preference and paranoia. I was a Windows user not so long ago and Peerguardian crashed a lot, leaving the system wide open. I haven't experienced this problem with moblock and Ubuntu.

Deluge 1.x is new and a complete rewrite. I has some nice new features, but last time I checked the blocklist plugin wasn't working yet, despite being shipped with the main application (I guess 1.06). 

You could test it by creating a blocklist with the range 0.0.0.0-255.255.255.255 then load it into Deluge, disable iplist and try to download a torrent. If it connects to a tracker or a peer, then it's not working, because this range should block all existing IPs.

Anyway, since you have already iplist, is not really a security issue. I'm using the one from Hardy repositories, because I want the blocklist working. I'm not sure about which version is in the Intrepid repositories, but you can download old versions from [[COLOR="DarkRed"]**Deluge's web site**[/COLOR]]("http://download.deluge-torrent.org/") if you want. 

> **darkcrawler said:**
> What list do you use in the Blocklist of Deluge? Thanks

I use a combination of lists, that I download with a script and merge using the old Peerguardian for Linux. 

If you are interested, here is a small script as an example:

```
#!/bin/bash

#download dcha_hacker list
wget --timeout=30 --tries=3 --timestamping --no-directories -O [COLOR="Red"]**/home/me/blocklists/source/**[/COLOR]ib-dcha-hacker.p2p http://list.iblocklist.com/?list=dcha_hacker

#download dcha_pedophiles list
wget --timeout=30 --tries=3 --timestamping --no-directories -O [COLOR="Red"]**/home/me/blocklists/source/**[/COLOR]ib-dcha-pedophiles.p2p http://list.iblocklist.com/?list=dcha_pedophiles

#download tbg-hijacked list
wget --timeout=30 --tries=3 --timestamping --no-directories -O [COLOR="Red"]**/home/me/blocklists/source/**[/COLOR]tbg-hijacked.gz http://tbg.iblocklist.com/Lists/Hijacked.zip

#extract the zip file
aunpack --extract-to=[COLOR="Red"]**/home/me/blocklists/source/**[/COLOR]tbg-hijacked.p2p [COLOR="Red"]**/home/me/blocklists/source/**[/COLOR]tbg-hijacked.gz

#cat and merge the lists
cat [COLOR="Red"]**/home/me/blocklists/source/**[/COLOR]ib-dcha-hacker.p2p \
[COLOR="Red"]**/home/me/blocklists/source/**[/COLOR]ib-dcha-pedophiles.p2p \
[COLOR="Red"]**/home/me/blocklists/source/**[/COLOR]tbg-hijacked.p2p \
| sed '/^#/d' | sed '/^$/d' | sed 's/ - /-/g' | sed 's/- /-/g' | sed 's/ -/-/g' | sudo peerguardnf -f [COLOR="Red"]**/home/me/blocklists/merged/**[/COLOR]blocklists-deluge.p2p

```

Please notice that I use **peerguardnf** command to merge the lists, so Peerguardian must be installed. Peerguardian is no longer maintained and I'm afraid it doesn't work in Intrepid, but as far as I remember, you can also use iplist to merge several lists and export them.

Additionally, the third list in the example needs to be extracted, so it has an extra command line. The sed commands are for cleaning the lists, by removing commented lines and spaces between ranges.

You can get several lists from [iBlocklist]("http://iblocklist.com/lists.php") website. The lists from bluetack's are down and suffering from other problems lately ([[COLOR="Red"]**see this thread**[/COLOR]]("http://ubuntuforums.org/showthread.php?t=803183")), so I strongly recommend using TBG lists from iBlocklist site.

Most important then using Deluge with blocklist plugin or not, is to load updated blocklists into iplist application.

---

### Post by darkcrawler on 2008-12-03
Time for changes.. :)

1)The blocklist plugin of Deluge wasn't working good, a lot of problem when importing the list, so i removed it and installed the version of the intrepid repository (0.5.don't remember)and as i can see the blocklist now works fine..

2)After reading your last post i decided to remove iplist and try to use moblock. No problem with the installation, and i solved the problem of Bluetack lists using the lists of iBlocklist site. (i found a very useful script to update the lists made by you in the Moblock thread ;) )

Now i'm testing, but i'm just quite happy because i keep deluge blocklist working, moblock seems to work good for now.

Thanks a lot

---

### Post by lovinglinux on 2008-12-03
> **darkcrawler said:**
> Time for changes.. :)

1)The blocklist plugin of Deluge wasn't working good, a lot of problem when importing the list, so i removed it and installed the version of the intrepid repository (0.5.don't remember)and as i can see the blocklist now works fine..

2)After reading your last post i decided to remove iplist and try to use moblock. No problem with the installation, and i solved the problem of Bluetack lists using the lists of iBlocklist site. (i found a very useful script to update the lists made by you in the Moblock thread ;) )

Now i'm testing, but i'm just quite happy because i keep deluge blocklist working, moblock seems to work good for now.

Thanks a lot

You are welcome.

It wasn't my intention to suggest removing iplist and installing moblock. I have used both applications and both do their job pretty nicely. Using one or the other is just a matter of preference. I do like moblock because it has some features like the custom iptables scripts, so I also setup my firewall through moblock's commands.

Please be aware that if you use a firewall manager like Firestarter, you must make sure the firewall is started BEFORE moblock. If you install mobloquer (moblock GUI), you can check the status of the iptables and moblock. You can also do this by command-line, with the command "sudo moblock-control status", to verify if moblock's rules are in the top of the iptables chains. Anyway, you probably already read this in moblock thread, but it doesn't hurt to tell you again :)

---

### Post by darkcrawler on 2008-12-04
> **lovinglinux said:**
> Please be aware that if you use a firewall manager like Firestarter, you must make sure the firewall is started BEFORE moblock. If you install mobloquer (moblock GUI), you can check the status of the iptables and moblock. You can also do this by command-line, with the command "sudo moblock-control status", to verify if moblock's rules are in the top of the iptables chains. Anyway, you probably already read this in moblock thread, but it doesn't hurt to tell you again :)

Yes, it doesn't hurt! ;)
I use ufw as firewall manager, i tried to load it after moblock (tested with "sudo moblock-control status" moblock rules are in the top of iptables chains) but here comes the trouble.. Doing this moblock doesn't filter IPs no more..
If i turn off ufw and restart moblock then it filters as usual.. What can i do?

---

### Post by lovinglinux on 2008-12-04
> **darkcrawler said:**
> Yes, it doesn't hurt! ;)
I use ufw as firewall manager, i tried to load it after moblock (tested with "sudo moblock-control status" moblock rules are in the top of iptables chains) but here comes the trouble.. Doing this moblock doesn't filter IPs no more..
If i turn off ufw and restart moblock then it filters as usual.. What can i do?

Best thing to do is set this thread as [SOLVED] and post this other question in the mboblock thread. I really don't know why it's not working, but you could also post the result of "moblock-control status" there, to allow checking what is wrong.

---

### Post by darkcrawler on 2008-12-05
This is the result of "moblock-control status":

```
Current iptables rules (this may take awhile):

Chain INPUT (policy DROP 13 packets, 1624 bytes)
 pkts bytes target     prot opt in     out     source               destination         
  463  187K ufw-before-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
   13  1624 ufw-after-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain FORWARD (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ufw-before-forward  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 ufw-after-forward  all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain OUTPUT (policy ACCEPT 1 packets, 267 bytes)
 pkts bytes target     prot opt in     out     source               destination         
  584  437K ufw-before-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    1   267 ufw-after-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain ufw-after-forward (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 3/min burst 10 LOG flags 0 level 4 prefix `[UFW BLOCK FORWARD]: ' 
    0     0 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain ufw-after-input (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 RETURN     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:137 
    0     0 RETURN     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:138 
    0     0 RETURN     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:139 
    1    52 RETURN     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:445 
    0     0 RETURN     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:67 
    0     0 RETURN     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:68 
    0     0 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0           ADDRTYPE match dst-type BROADCAST 
   11  1441 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 3/min burst 10 LOG flags 0 level 4 prefix `[UFW BLOCK INPUT]: ' 
   12  1572 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain ufw-after-output (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    1   267 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain ufw-before-forward (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ufw-user-forward  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain ufw-before-input (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     all  --  lo     *       0.0.0.0/0            0.0.0.0/0           
  448  185K ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           ctstate RELATED,ESTABLISHED 
    0     0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           ctstate INVALID 
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 3 
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 4 
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 11 
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 12 
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp spt:67 dpt:68 
   15  1724 ufw-not-local  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 ACCEPT     all  --  *      *       224.0.0.0/4          0.0.0.0/0           
    0     0 ACCEPT     all  --  *      *       0.0.0.0/0            224.0.0.0/4         
   15  1724 ufw-user-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
   13  1624 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain ufw-before-output (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     all  --  lo     *       0.0.0.0/0            0.0.0.0/0           
  555  433K ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           state NEW,RELATED,ESTABLISHED 
   28  3612 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           state NEW,RELATED,ESTABLISHED 
    1   267 ufw-user-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    1   267 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain ufw-not-local (1 references)
 pkts bytes target     prot opt in     out     source               destination         
   15  1724 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0           ADDRTYPE match dst-type LOCAL 
    0     0 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0           ADDRTYPE match dst-type MULTICAST 
    0     0 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0           ADDRTYPE match dst-type BROADCAST 
    0     0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 3/min burst 10 LOG flags 0 level 4 prefix `[UFW BLOCK NOT-TO-ME]: ' 
    0     0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain ufw-user-forward (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain ufw-user-input (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    2   100 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:6881 
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:6882 
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:6883 
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:6884 
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:6885 
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:6886 
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:6887 
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:6888 
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:6889 
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:4662 
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:4672 
   13  1624 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain ufw-user-limit (0 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 3/min burst 5 LOG flags 0 level 4 prefix `[UFW LIMIT]: ' 
    0     0 REJECT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           reject-with icmp-port-unreachable 

Chain ufw-user-limit-accept (0 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain ufw-user-output (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    1   267 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Please check if the above printed iptables rules are correct!

 * moblock is running, pid is 10435.

```

is there something wrong?

---

### Post by lovinglinux on 2008-12-05
> **darkcrawler said:**
> is there something wrong?

Yes, there is something wrong with my brain.](*,)

I don't know why, but I told you to do exactly the opposite of what you should do. You must start moblock AFTER the firewall.:oops:

I have already fixed the instructions on previous posts, but you still have a quote of my text on one of your posts with the incorrect instructions. So if you don't mind, could you please delete it? 

How ironic is my comment "it doesn't hurt"?

---

### Post by darkcrawler on 2008-12-05
I just fixed your instructions in the quote, now it's right! ;)
When i used ipblock i always started it manually after ufw(loaded on boot) and it always worked good, and i thought it should be the same with moblock.. i was right!
Don't worry for that, we easily solved the trouble ;)
Anyway.. It doesn't hurt! :D

---

### Post by lovinglinux on 2008-12-05
> **darkcrawler said:**
> I just fixed your instructions in the quote, now it's right! ;)
When i used ipblock i always started it manually after ufw(loaded on boot) and it always worked good, and i thought it should be the same with moblock.. i was right!
Don't worry for that, we easily solved the trouble ;)
Anyway.. It doesn't hurt! :D

Thanks.

If you are willing to learn iptables rules, you can use "/etc/moblock/iptables-custom-insert.sh" and "/etc/moblock/iptables-custom-remove.sh" to create and remove iptables rules, when starting and stopping moblock respectively. Then you can completely disable ufw and set moblock to start at boot. This way you can forget about the order thing, since moblock will handle all the iptables for you. No need to use two applications to control your network traffic.

My "/etc/moblock/iptables-custom-remove.sh" is set to block all network traffic, so whenever moblock stops I'm completely secure and when it starts it launches all my custom rules.

---

### Post by darkcrawler on 2008-12-05
> **lovinglinux said:**
> Thanks.

If you are willing to learn iptables rules, you can use "/etc/moblock/iptables-custom-insert.sh" and "/etc/moblock/iptables-custom-remove.sh" to create and remove iptables rules, when starting and stopping moblock respectively. Then you can completely disable ufw and set moblock to start at boot. This way you can forget about the order thing, since moblock will handle all the iptables for you. No need to use two applications to control your network traffic.

This is exactly what i'd like to do, disable the firewall manager and give to moblock all the network control.. At the moment i don't know how to use "/etc/moblock/iptables-custom-insert.sh" and "/etc/moblock/iptables-custom-remove.sh", but i think i'll find about them in the moblock general thread..

> **lovinglinux said:**
> 
My "/etc/moblock/iptables-custom-remove.sh" is set to block all network traffic, so whenever moblock stops I'm completely secure and when it starts it launches all my custom rules.

Sounds good.. :-k

---

### Post by lovinglinux on 2008-12-05
> **darkcrawler said:**
> This is exactly what i'd like to do, disable the firewall manager and give to moblock all the network control.. At the moment i don't know how to use "/etc/moblock/iptables-custom-insert.sh" and "/etc/moblock/iptables-custom-remove.sh", but i think i'll find about them in the moblock general thread.

"/etc/moblock/iptables-custom-remove.sh" runs automatically by default when you stop moblock in the mobloquer GUI or via command "sudo moblock-control stop".

 "/etc/moblock/iptables-custom-insert.sh" runs automatically by default when you start moblock in the mobloquer GUI or via command "sudo moblock-control start".

Both run automatically when you restart moblock via GUI or the command "sudo moblock-control restart". In this case, "/etc/moblock/iptables-custom-remove.sh" runs first.

So all you have to do is put the iptables rules inside those files.

[[COLOR="Red"]**Here**[/COLOR]]("http://ubuntuforums.org/showthread.php?t=159661") you can learn more about iptables rules.

These are my basic rules:

"/etc/moblock/iptables-custom-remove.sh"

```
iptables -F
iptables -X
iptables -P INPUT DROP 
iptables -P OUTPUT DROP
iptables -P FORWARD DROP
```

The first line flushes the current rules, the second remove custom chains and the others set the default rule for the 3 default chains to DROP, thus locking up the firewall.

 "/etc/moblock/iptables-custom-insert.sh"

I have included comments in the code. 

```


# create custom chains to receive blocked traffic and log them
iptables -N INBOUND
iptables -N OUTBOUND

# set the default rules to deny traffic
iptables -P INPUT DROP 
iptables -P OUTPUT DROP
iptables -P FORWARD DROP

# set the rules for the default INPUT chain 
iptables -A INPUT -p icmp -j INBOUND # send icmp to the logging chain
iptables -A INPUT -i eth0 -p tcp -m state --state ESTABLISHED,RELATED -j ACCEPT # accept tcp inbound related to established connections
iptables -A INPUT -i eth0 -p udp -m state --state ESTABLISHED,RELATED -j ACCEPT  # accept udp inbound related to established connections
iptables -A INPUT -i lo -j ACCEPT # accept connections on the loopback
iptables -A INPUT -j INBOUND  # send the remaining packets to the logging chain
iptables -A INPUT -j DROP #deny everything else

# set the rules for the default FORWARD chain 
iptables -A FORWARD -j DROP #deny everything because my machine does not act like a router

# set the rules for the default OUTPUT chain 
iptables -A OUTPUT -o eth0 -p tcp -m state --state ESTABLISHED,RELATED -j ACCEPT # allow tcp outgoing packets for established connections
iptables -A OUTPUT -o eth0 -p udp -m state --state ESTABLISHED,RELATED -j ACCEPT # allow udp outgoing packets for established connections
iptables -A OUTPUT -o eth0 -p tcp -m tcp --dport 53 -j ACCEPT # allow tcp DNS queries
iptables -A OUTPUT -o eth0 -p udp -m udp --dport 53 -j ACCEPT  # allow udp DNS queries
iptables -A OUTPUT -o eth0 -p tcp -m tcp --dport 80 -j ACCEPT #allow http
iptables -A OUTPUT -o eth0 -p udp -m udp --dport 80 -j ACCEPT #allow http
iptables -A OUTPUT -o eth0 -p tcp -m tcp --dport 443 -j ACCEPT #allow https
iptables -A OUTPUT -o eth0 -p udp -m udp --dport 443 -j ACCEPT #allow https
iptables -A OUTPUT -o eth0 -p tcp -m tcp --dport 993 -j ACCEPT #allow imap
iptables -A OUTPUT -o eth0 -p udp -m udp --dport 993 -j ACCEPT #allow imap
iptables -A OUTPUT -o eth0 -p tcp -m tcp --dport 6667 -j ACCEPT #allow irc
iptables -A OUTPUT -o eth0 -p udp -m udp --dport 6667 -j ACCEPT #allow irc
iptables -A OUTPUT -o eth0 -p tcp --dport 22 -j ACCEPT #allow ssh
iptables -A OUTPUT -o lo -j ACCEPT #allow loopback
iptables -A OUTPUT -p icmp -j ACCEPT #allow icmp
iptables -A OUTPUT -j OUTBOUND #send the rest to the logging chain
iptables -A OUTPUT -j DROP #drop everything else

# set the rules for logging and dropping chains, which receives all traffic not dropped, rejected or accepted from the other chains above
iptables -A INBOUND -p tcp -j LOG --log-prefix '     INBOUND TCP     ' --log-level 4 
iptables -A INBOUND -p tcp -j DROP
iptables -A INBOUND -p udp -j LOG --log-prefix '     INBOUND UDP     ' --log-level 4 
iptables -A INBOUND -p udp -j DROP
iptables -A INBOUND -p icmp -j LOG --log-prefix '     INBOUND ICMP    ' --log-level 4
iptables -A INBOUND -p icmp -j DROP
iptables -A INBOUND -m state --state INVALID -j LOG --log-prefix '     INBOUND INVALID     ' --log-level 4
iptables -A INBOUND -m state --state INVALID -j DROP
iptables -A INBOUND -j LOG --log-prefix '     INBOUND OTHER     ' --log-level 4
iptables -A INBOUND -j DROP


iptables -A OUTBOUND -p tcp -j LOG --log-prefix '     OUTBOUND TCP     ' --log-level 4
iptables -A OUTBOUND -p tcp -j REJECT
iptables -A OUTBOUND -p udp -j LOG --log-prefix '     OUTBOUND UDP     ' --log-level 4
iptables -A OUTBOUND -p udp -j REJECT
iptables -A OUTBOUND -p icmp -j LOG --log-prefix '     OUTBOUND ICMP    ' --log-level 4
iptables -A OUTBOUND -p icmp -j REJECT
iptables -A OUTBOUND -m state --state INVALID -j LOG --log-prefix '     OUTBOUND INVALID     ' --log-level 4
iptables -A OUTBOUND -m state --state INVALID -j REJECT
iptables -A OUTBOUND -j LOG --log-prefix '     OUTBOUND OTHER     ' --log-level 4
iptables -A OUTBOUND -j REJECT
```

These rules are not intended for copying and pasting, but for educational purposes. Read the tutorial about iptables first, then analyze these rules to understand what they are doing. 

When you start moblock it also inserts other chains and rules that are related to the IP blocking feature. These rules are included in the top of the default chains, so all traffic is first filtered by the ip blocklists. If not blocked, then a packet proceeds into the chain of the rules above, until it encounters a matching rule, when it can be accepted, dropped, rejected or send to another chain like my INBOUND and OUTBOUND chains, where everything is logged and dropped.

I hope this help.

---

### Post by jre on 2009-01-10
@lovinglinux: I just wondered if you are using ACCEPT in your iptables rules, but should use RETURN instead. ACCEPT means accept now, no further examination by other iptables rules. RETURN means "personally I would accept it, but let's look what further iptables rules say about it."
Probably you know what you do and I didn't have a close enough look at your rules. Still then I want to warn other users to be aware of the difference.
Greets!
jre

---

### Post by lovinglinux on 2009-01-10
> **jre said:**
> @lovinglinux: I just wondered if you are using ACCEPT in your iptables rules, but should use RETURN instead. ACCEPT means accept now, no further examination by other iptables rules. RETURN means "personally I would accept it, but let's look what further iptables rules say about it."
Probably you know what you do and I didn't have a close enough look at your rules. Still then I want to warn other users to be aware of the difference.
Greets!
jre

Thanks for the advice. I understand the difference between ACCEPT and RETURN, but I'm not sure if I should use RETURN instead. As far as I understand, RETURN is useful for example for rules created by moblock because packets not filtered by the ip block list will return to the chain and then analyzed for other conditions like destination port and protocol, by the rules created by the firewall manager or the iptables scripts. But since my ACCEPT rules are below moblock's rules, below my DROP rules and don't have very complex condition filters, wouldn't be enough to use ACCEPT? 

For example, if I open port 6881 for p2p moblock will catch the traffic first and filter by IP, returning those packets with allowed ips to the chain. Then if I have a rule accepting packets on port 6881, all packets returned by moblock will be immediately accepted. Isn't this exactly what I need?

I also have some rules to block incoming ICMP, invalid packets and other stuff. These rules are above the ACCEPT rules, so the packets that satisfy these conditions will be blocked even if moblock return them and even if I have the ACCEPT rule for the destination port.

Please tell me what you think. I don't have much experience with iptables, so it's easy to make a stupid mistake and mess things up.

---

### Post by jre on 2009-01-11
I think you have done it absolutely correctly.

---

