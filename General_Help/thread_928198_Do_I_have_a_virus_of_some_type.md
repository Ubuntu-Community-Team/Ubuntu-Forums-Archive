---
title: "Do I have a virus of some type?"
date: 2008-09-23
forum: General Help
---

### Post by danbuter on 2008-09-23
I ran chkrootkit and got the following result:
Checking `sniffer'... lo: not promisc and no packet sniffer sockets
eth0: PACKET SNIFFER(/sbin/dhclient3[5807])
Checking `w55808'... not infected

I'm not sure if the eth0 line means I have a problem or not. Anyone know? Thanks!

---

### Post by AllanPoe on 2008-09-23
Check this tread [http://ubuntuforums.org/showthread.php?t=270340]("http://ubuntuforums.org/showthread.php?t=270340")

---

### Post by Sef on 2008-09-23
From [Nabble.com]("http://www.nabble.com/understanding-chkrootkit-and-rkhunter-logs-td10379361.html"), read this below:

> > eth0: PACKET SNIFFER(/sbin/dhclient[2181]) 
You don't need to worry about this if you're really obtaining your IP  
address via DHCP on eth0. dhclient really acts as a packet sniffer (it  
listens in promisc mode) but that's normal. 

---

