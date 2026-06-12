---
title: "Combining ethernet connections."
date: 2008-09-19
forum: General Help
---

### Post by yousillygoose on 2008-09-19
Hello all.

I'll start off with a little background: the school I go to has terrible internet.  We are capped at 170kb/s download (which we can only ever reach overnight due to the limited total bandwidth).  During daytime hours we may only be able to reach 20-50 kb/s.  Each room also only has one ethernet jack.  I bought a splitter for hooking up multiple computer and have learned that each computer gets a unique IP and also its own bandwidth allotment.  Finally, my school has a packet shaper that blocks torrents, irc, etc. The only way to get around the packet shaper is to encrypt the packets in whatever application you are using.

That all being said I have an old Pentium 3 server that I use as a downloading machine.  Generally I download large files off campus at my house (via SSH) and then transfer them onto campus via a secure encrypted connection.  The problem with this is that I can only download from my house at 50kb/s because if I go to high my family feels the internet downspeed going downhill.  If I try to download torrents on campus (using an encrypted connection) speeds also suffer due to a crappy school connection (I am testing it now by downloading the same file at my house and on campus at the same time).  The file on campus is UP/DN 50/20.  The file at my friends house is 40/80.

I have read a bunch about combining ethernet cards via bridging or bonding to potentially double your bandwidth.  I learned that you can use both connections at the same time and trade off parts downloaded, you can have have 1 card solely handle one activity when the other card handles the rest, etc.

So, here is my questions for you:
1. If I combined the two cards to work hand in hand would that increase my torrenting speed or would torrents not be able to utilize multiple cards.
2. Which way would you combine these cards and how.

THANK YOU ALL FOR THE HELP (IN ADVANCED).

---

### Post by LowSky on 2008-09-19
You have one ethernet jack into your room, how are you going to utilize two ethernets cards, because if you use a router or a switch all it is going to do is divide the bandwith up.

---

### Post by yousillygoose on 2008-09-19
bump!

---

### Post by yousillygoose on 2008-09-19
sorry about that bump.  for some reason your post didn't show up.  The switch just splices the connection and makes the college network see it as many man (16 to be exact) extra ports.  Each port gets full bandwidth and a unique IP.

---

### Post by zxscooby on 2008-09-20
I am also interested in this.

---

### Post by yousillygoose on 2008-09-20
Yay!!!! more people like my interests

---

### Post by yousillygoose on 2008-09-21
Bumps

---

### Post by yousillygoose on 2008-10-07
gonna bump this again......

---

### Post by yousillygoose on 2008-10-07
I will throw out that I have a separate question: on my college network each network card gets a different IP address.  Would it be possible to put more ethernet cards in my computer and make the computer have more than 1 ip address?

---

### Post by lisati on 2008-10-07
> **yousillygoose said:**
> sorry about that bump.  for some reason your post didn't show up.  The switch just splices the connection and makes the college network see it as many man (16 to be exact) extra ports.  Each port gets full bandwidth and a unique IP.

> **LowSky said:**
> You have one ethernet jack into your room, how are you going to utilize two ethernets cards, because if you use a router or a switch all it is going to do is divide the bandwith up.

Please forgive me if I'm missing something here: wouldn't there be some kind of practical limit on bandwidth if two or more ports are accessed through one ethernet cable, even if you managed to configure the different NIC cards in the machines on one end to be seen as different machines/ports, each with its own cap, by the "host" at the other end?

---

### Post by yousillygoose on 2008-10-07
my college internet does its bandwidth cap by ip addresses.  I have 3 computers running in my room all with their own bandwidth cap through a switch.  So, each IP is like a whole new connection.  Would it be possible to have the computer seem like 2 different computers to the network by containing 2 ip addresses?

---

### Post by y@w on 2008-10-07
Ok, yes you can do that and it will give you a speed boost for traffic where the bottleneck is your local network. If you have one physical link back to the school's switch then bonding won't help at all. If they are limiting you per switch port and you have access to multiple ports, then I'd do NIC bonding like this: [http://www.cyberciti.biz/tips/linux-bond-or-team-multiple-network-interfaces-nic-into-single-interface.html](http://www.cyberciti.biz/tips/linux-bond-or-team-multiple-network-interfaces-nic-into-single-interface.html)

---

### Post by yousillygoose on 2008-10-07
but is there any way it can use the two connetions separately while having them both up at the same time.  I want to run two proxy servers on it for each separate IP address.

---

### Post by y@w on 2008-10-07
> **yousillygoose said:**
> but is there any way it can use the two connetions separately while having them both up at the same time.  I want to run two proxy servers on it for each separate IP address.

So you want them to operate separately yet together at the same time? I don't think so.. If you can get two connections to your machine, is there something stopping you from getting three? You could run two NICs bonded and the third on a separate IP..

---

### Post by yousillygoose on 2008-10-07
I can get as many as slots I have to fit more network cards.  Each new card would get it's own IP address.  I want to be able to talk to the computer from each IP address independently.  I am kinda trying to build a low-level proxy server

---

