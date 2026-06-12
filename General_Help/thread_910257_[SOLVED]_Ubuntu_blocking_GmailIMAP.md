---
title: "[SOLVED] Ubuntu blocking Gmail/IMAP?"
date: 2008-09-04
forum: General Help
---

### Post by *B* on 2008-09-04
I have 2 dual boot systems with XP & a fully updated Ubuntu. I have a FAT32 partition on each system to share files and folders easily with Ubuntu. I keep my Thunderbird and Firefox profiles on these Fat32 partitions so I have the exact same programs/settings/mail in Xp or Ubuntu. 

I recently changed my Gmail accounts over to IMAP and got everything setup in Thunderbird, in XP. Everything works fine in XP. When I boot to Ubuntu and open Thunderbird, I get the "could not connect to mail server imap.gmail.com; the connection was refused" error message.... BEFORE Thunderbird even asks for my master password. Since this is the same profile I use in XP, I know the settings I used from Google's own setup page work:

Incoming:
Server Type: IMAP Mail Server
Server Name: imap.gmail.com
Port: 993
User Name: myuserhere
Use secure connection: SSL
Use secure authentication: unchecked

Outgoing:
Server Name: smtp.gmail.com
Port: 465
Use name and password: checked
User Name: myfullemailaddyhere
Use secure authentication: SSL

Now, when I try to send an email through one of my IMAP accounts, I get this message:

"Sending of message failed. The message could not be sent because connecting to SMTP server smtp.gmail.com failed. The server may be unavailable or is refusing SMTP connections. Please verify that your SMTP server setting is correct and try again, or else contact your network administrator."

Now, here is the kicker.... lmao. Every since the last Ubuntu update, I havent been able to access any google site in Firefox 3.01 either. I cant even ping or traceroute imap.google.com or google.com when I am in Ubuntu. All these things work just fine when booted to windows using the same exact shared profiles for Tb & FF... which I have been doing for a long time.

Now remember, all these settings work in XP, so I know its not a connection or setting issue, unless Ubuntu doesnt like the port setting. Any help is GREATLY appreciated.

---

### Post by *B* on 2008-09-05
Well, this has to be a Ubuntu thing. I started over in Ubuntu with a totally new profile and set up all my accounts again to make sure it wasnt something that the Linux version of TB didnt like about the profile it was sharing with XP. Same result. My standard POP account with my local ISP works fine.... the IMAP Gmail accounts still give the same "could not connect" error before the master password prompt is even displayed. there is one error message for each of the accounts. After exiting out of the error messages, I can then sign in with my master password. 

On a similar note, I also started over from scratch with my Firefox profile in Linux and stopped sharing the profile from XP. Same thing there...... even with a frash profile and nothing else installed (no other extensions or themes) I cannot connect to any google site. 

Any ideas what is going on?

---

### Post by cariboo on 2008-09-05
Check your /etc/resov.conf file to make sure your dns isn't being redirected somewhere else other then your isp.

Jim

---

### Post by jerome1232 on 2008-09-05
edit: I'm to slow lol

My first thought is DNS, can you post the output of the following:
that second to last ip is one of google.com's ips, the last one is imap.gmail.com's ip.
```
nslookup google.com
cat /etc/hosts
cat /etc/resolv.conf
ping -c 4 64.233.187.99
ping -c 4 64.233.185.109
```


If you get permision denied on any of those just prepend the command with sudo but you should have read access to all of those files.

---

### Post by *B* on 2008-09-05
First off, thanks for the replies. Secondly, here is the info you asked for. The only thing I found out of the ordinary is that "#53" at the end of the DNS number. That doesnt show under network settings/DNS.

nslookup google.com
Server:		209.142.136.220
Address:	209.142.136.220#53

Non-authoritative answer:
Name:	google.com
Address: 72.14.207.99
Name:	google.com
Address: 64.233.167.99
Name:	google.com
Address: 64.233.187.99


cat /etc/hosts
127.0.0.1 localhost
127.0.1.1 Tower1-Ubuntu.workgroup

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts


cat /etc/resolv.conf
domain workgroup
nameserver 209.142.136.220
nameserver 208.54.220.20


ping -c 4 64.233.187.99
PING 64.233.187.99 (64.233.187.99) 56(84) bytes of data.
From 192.168.1.13 icmp_seq=1 Destination Port Unreachable
From 192.168.1.13 icmp_seq=2 Destination Port Unreachable
From 192.168.1.13 icmp_seq=3 Destination Port Unreachable
From 192.168.1.13 icmp_seq=4 Destination Port Unreachable

--- 64.233.187.99 ping statistics ---
4 packets transmitted, 0 received, +4 errors, 100% packet loss, time 3000ms


ping -c 4 64.233.185.109
PING 64.233.185.109 (64.233.185.109) 56(84) bytes of data.
From 192.168.1.13 icmp_seq=1 Destination Port Unreachable
From 192.168.1.13 icmp_seq=2 Destination Port Unreachable
From 192.168.1.13 icmp_seq=3 Destination Port Unreachable
From 192.168.1.13 icmp_seq=4 Destination Port Unreachable

--- 64.233.185.109 ping statistics ---
4 packets transmitted, 0 received, +4 errors, 100% packet loss, time 2999ms


P.S. just a side note - I have tried other DNS #'s, even those from openDNS but have the same result.

---

### Post by jerome1232 on 2008-09-05
Okay so DNS works just fine you just can't get any traffic out, can you ping other websites by name like yahoo.com, ubuntuforums.org, etc...

Is this only with google webistes?

Did you set up a firewall, or some sort of domain filter, either software or in your router. Did you setup some sort of proxy? Look at System>>Preferences>>Proxy Settings and see if something is amiss there (I haven't used gnome for a bit so it could be proxy, proxies or something different)

As for the firewall can you post the output of iptables, I'm mostly looking for entries in the OUTGOING rules.

```
sudo iptables -L -v
```

---

### Post by *B* on 2008-09-05
Ok, I REALLY feel like a dummy now. Believe me, Im not the type to post for help immediately, I try to exhaust all avenues myself before I do... but I feel SO stupid now. As soon as I saw your question about IP tables, I KNEW what the problem was. I had installed Azureus a few months ago because I had read I could import the lists from PG2. When I couldnt import the lists, I installed MoBlocker. Even though I havent used Azureus since, I guess MoBlocker updated and started blocking several IP addys... google and yahoo to name a few. I removed MoBlocker through synaptic and all seems to be fine now. Thank you so much for your help, and again.... apologies from a 15 year M$ user trying to learn something new.

---

### Post by jerome1232 on 2008-09-05
hehe, no worries I've installed a program before that came back to bite me with network problems 3 months later. 

Glad you got it figured out.

---

