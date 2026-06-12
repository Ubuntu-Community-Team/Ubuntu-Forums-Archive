---
title: "Ubuntu Hacked or virus"
date: 2008-11-19
forum: General Help
---

### Post by dennis_k85 on 2008-11-19
It appears my Ubuntu system has been hacked or infected with a virus, that responds on UDP port 9977. I was getting hit with about 20 or 30 packets a minutes from different IP addresses. My system is behind a firewall, which seems wierd unless it is somehow initiating the connections. 

One of the IP addresses resolved back to: [https://code.plan-b.ru](https://code.plan-b.ru)
 which is password protected. 

Has anyone else seen anything like this?

My system is fully up to date. 

Dennis

---

### Post by amauk on 2008-11-19
have you installed apt-p2p?
reason I ask, is that runs over port 9977

---

### Post by dracayr on 2008-11-19
Definitely seems like DOS or DDOS attack. code.plan-b.ru may be password protected, but plan-b.ru not. It's some projekt that's got sth. to do with IT, but theres not very much information on the site (and I had to use the google translator). The page doesn't seem to be very secure, though, which seems strange for a hacker group: [http://plan-b.ru/news/journey/](http://plan-b.ru/news/journey/)

EDIT: Just saw the title of this thread. Just because your system is 'under attack', it doesn't mean its already 'hacked'

dracayr

---

### Post by dennis_k85 on 2008-11-19
Actually it does mean my system has been compromised. Because these packets on port 9977 are getting through my linksys firewall and getting to my ubuntu system. Which means more than likely my ubuntu system initiated the connection, but I don't see it on my filewall logs. 

Actually I did install apt-p2p about a week ago. I will try removing it later to see if that is the problem. If it is having it installed seems to have a huge affect on my network. 

Dennis

---

### Post by DGortze380 on 2008-11-19
> **dennis_k85 said:**
> Actually it does mean my system has been compromised. Because these packets on port 9977 are getting through my linksys firewall and getting to my ubuntu system. Which means more than likely my ubuntu system initiated the connection, but I don't see it on my filewall logs. 

Actually I did install apt-p2p about a week ago. I will try removing it later to see if that is the problem. If it is having it installed seems to have a huge affect on my network. 

Dennis

You have a firewall. If the port is unused, shut it down. Or add some rules and block the IPs. If they're close enough together and all Russian IPs (assuming you don't need any legitimate access from a Russian IP), just block the whole subnet.

---

### Post by dennis_k85 on 2008-11-20
I removed apt-p2p. And I was still getting incoming packets on 9977. They stop as soon as I shut down my Ubuntu system. And they don't start until I restart my Ubuntu system. My fire wall is blocking them now, but I get so many packets coming in that it kill my network performance. 

Does anybody have any idea what could sending requests from Ubuntu. I have Crossover installed. Could it be a windows virus? 

At this point I have to leave my Ubuntu system turned off, otherwise my firewall gets hammered with packets on port 9977. 

Help?????

---

