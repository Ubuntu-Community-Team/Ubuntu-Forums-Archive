---
title: "samba question"
date: 2006-02-04
forum: Installation &amp; Upgrades
---

### Post by wwuster on 2006-02-04
I have samba working great but I do have a problem getting it to start up. I have Ubuntu and winxp connected. Zone alarm runs on windows and iptables runs in Ubuntu (I use firestarter to configure it).

When I first boot the machines I have to turn off both firewalls to get the initial samba connection. After that I can turn both firewalls back on and it works from then on until the next reboot. I've turned on samba services using firestarter. How can I stop having to turn off the firewalls to get the initial connection?

thanks,
William

---

### Post by alamba on 2006-02-04
If u're on private IP's...try connecting to samba from your XP box. Open firefox. Under events, right click on the blocked samba connection and click on allow from this host.

Akshay

---

### Post by wwuster on 2006-02-04
This should have nothing to do with firefox. I initially connect with windows explorer or from the command line. I have ubuntu mapped as drive x.

William

---

### Post by alamba on 2006-02-04
oops sorry....firestarter

A

---

### Post by wwuster on 2006-02-05
When I rebooted today I started Ubuntu and firestarter first. I also ran tcpdump
while I started winxp. After windows started I turned off it's firewall and tried to see the files on Ubuntu and windows couldn't see them. I then checked the output of tcpdump back on Ubuntu and got a few of these:

IP 192.168.1.101.137 > 192.168.1.255.137: NBT UDP PACKET(137): QUERY; REQUEST; BROADCAST

Port 137 is supposed to be allowed in the samba services (inbound traffic policy). Also, I allow all connections from 192.168.1.101.

So why do I have to turn off the Ubuntu firewall completely before samba works?

William

---

### Post by alamba on 2006-02-06
U don't...AFAIK u're just blocking a port you shouldn't be. I would cross check if you actually allow all connections/packets from 101.

A

---

### Post by wwuster on 2006-02-06
Maybe it has something to do with the inbound traffic policy rule.

In firestarter I have "When the source is"
IP, host, or network:
192.168.1.101/32,

but from tcpdump I see 192.168.1.255 source packets. I don't see any events listed. If that's the problem how can I add this (broadcast?) address to the inbound traffic policy. I would like to be very rescrictive and only allow this one machine on my LAN to connect.

Thanks,
William

---

### Post by wwuster on 2006-02-06
Now that I had a clue what to search for in the forums I found what I think will be the solution. I didn't read this in any samba howto's. It was about broadcasting...

[http://ubuntuforums.org/showthread.php?t=24440&pp=10](http://ubuntuforums.org/showthread.php?t=24440&pp=10)

William

---

