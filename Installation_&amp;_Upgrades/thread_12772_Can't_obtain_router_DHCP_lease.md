---
title: "Can't obtain router DHCP lease"
date: 2005-01-26
forum: Installation &amp; Upgrades
---

### Post by jwitalka on 2005-01-26
My Ubuntu desktop install worked fine except I can't make DHCP via a Motorolla WR850G router work.  I'm using a wired connection via a DLink DFE530TX plus Eternet card.  I also have Windows installed on the same PC and it can obtain a DHCP lease with no problems, so the connection is OK.  I can't Ping the router (192.168.10.1) and I get a connection refused when I try to access the router via Firefox.

Don't remember the exact install error message, but it said something about not being able establish a network connection.  I continued on and the rest of the install went fine. I've tried Red hat and SUSE and get the same errors.  I've also tried a Linksys and a Belkin Ethernet NIC with no better results.  

Any ideas on what to try?  I'm a Linux newbie.

---

### Post by rudi on 2005-01-26
is your adapter recognized by Ubuntu?
 Use the command **lsmod** to see if your NIC is listed (it is a bit cryptic, but you should recognize it if it's there)

---

### Post by jwitalka on 2005-01-26
I don't see anything that looks like an ethernet card. At bott time I do see an attempt to initialze a RTL8129/8139  that the Dlink 530tx+ is based on.  Don't see an error message until Ubuntu attempts a Clock synchronization and gets a DNS error.

---

### Post by rudi on 2005-01-26
I'm sorry, but i don't really understand, could you use the command **dmesg, **to see if your card is recognized and initialized? Look for something like this (my dmesg output for a 3COM NIC):
   ```
eth0: 3Com Gigabit LOM (3C940)
  	  PrefPort:A  RlmtMode:Check Link State
  NET: Registered protocol family 17
  eth0: network connection up using port A
  	speed:		   100
  	autonegotiation: yes
  	duplex mode:	 full
  	flowctrl:		symmetric
  	irq moderation:  disabled
  	scatter-gather:  enabled
  	tx-checksum:	 enabled
  	rx-checksum:	 enabled
  NET: Registered protocol family 10
  Disabled Privacy Extensions on device c02eb8a0(lo)
  IPv6 over IPv4 tunneling driver
``` 
   
   If you don't see anything similar, i think you have to install a driver manually.
 
 [edit]You might want to look at your /etc/resolv.conf file. Your nameserver is listed there.[/edit]

---

