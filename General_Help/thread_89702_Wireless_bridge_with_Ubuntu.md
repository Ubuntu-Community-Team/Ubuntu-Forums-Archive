---
title: "Wireless bridge with Ubuntu"
date: 2005-11-13
forum: General Help
---

### Post by Tipenso on 2005-11-13
Hi to all.
I'm still trying to set a wireless bridge on a Ubuntu box.
My project:
I have two LAN segments, LAN A (192.168.0.0/24) with some PCs, and LAN B (192.168.1.0/24), with some PCs and an access point (192.168.1.254).
Two segments are in different and far rooms.
In LAN A, I have an Ubuntu linux box with two ethernet cards, 1 wired (eth0) and 1 wireless (wlan0). I've installed bridge-utils, so have I created a bridge br0 (it has ip 192.168.0.254), which include eth0 and wlan0 (as I read in some how-to, I give them ip address 0.0.0.0).
Results:
from everywhere in A I can ping br0, from everywhere in B I can ping br0, from linux box with br0 I can ping everything in A and B, but I can't ping B from A and vice-versa (that is the goal I would to reach!).
I've tried everything, but without success.
What could be the problem? Could it be an iptables issue? I've never configured iptables, so its state is as in default Ubuntu installation. Is Ubuntu firewall active in default installation?
Or could it be another problem?
Thanks in advance for your help.

---

### Post by slux on 2005-11-13
You have a configuration with two different networks and a bridge isn't going to help with that as it only operates on the link layer. You either need to configure all machines to be on the same network after which the bridging setup should work or let the ubuntu box act as a router between the two networks.

---

### Post by Tipenso on 2005-11-13
Thanks for answer.
Ok, I put Lan B in the same network as Lan A (192.168.0.0/24).
Now all PCs, access point and linux box are in the same network, but I continue to have same problems: Lan A can ping the bridge, Lan B can ping the bridge, the bridge can ping everything, but Lan A can't ping Lan B and vice-versa.
Must I particular routes and/or default gateway configure?
Now I have only route
> 192.168.0.0               *               255.255.255.0   U     0      0        0 br0

Thanks in advance.

---

### Post by slux on 2005-11-13
There should be no need for configuring routes for bridging as the bridge should forward the packets as required between the networks at the ethernet level (at a lower level than the IP protocol).

I must admit that I am not familiar with bridge-utils, I've only used Proxy ARP for bridging on Linux myself but it seems to me that your problem relates to it not being configured properly.

---

### Post by gnottage on 2005-11-14
I'm interested in this since I am trying to do a similar thing, albeit with slight differences...

Downstairs I have a cable mode and wireless router (802.11a/b/g) connected (wired) to a single PC.

I have a laptop with 802.11a/b/g which is dual boot XP Pro and Ubuntu. All over the house I can get online with either a or g. This is my test machine as it has a wireless card and wired ethernet already.

Upstairs I have 4 PCs and a printer connected with a switch. Also at present at the moment is an access point that bridges 802.11g. I want to move to 802.11a only as 2.4GHz interferes with DECT phones. I've brought another AP that does 802.11a, but in the EU the firmware wont allow me to bridge. So I think about trying this in software. Yesterday I tried under WinXP, but it never realised that I wanted to use both wired and wireless at once (kept selecting the wired as it was "faster" despite not having internet connectivity).

So I booted up Ubuntu and tried out bridging. All the PCs have 192.168.1.x IP addresses, and my findings were just like Tipenso's. This must be possible...

---

### Post by Tipenso on 2005-11-14
These are commands I gave to make the bridge:
> ifconfig eth0 down
ifconfig wlan0 down
brctl addbr br0
brctl addif br0 eth0
brctl addif br0 wlan0
ifconfig eth0 0.0.0.0 up
ifconfig wlan 0.0.0.0 up
ifconfig br0 192.168.0.253 netmask 255.255.255.0 up
I try also promiscuous mode on all two interfaces:
> ifconfig eth0 promisc
ifconfig wlan0 promisc
No results.
This issue could be useful also to connect wirelessly Xbox or Ps2 without buy a wireless game adapter (I had this idea this night for my Xbox)...
So, come on ubuntu girls and boys, let's try!!!
Your ideas are welcome.

---

