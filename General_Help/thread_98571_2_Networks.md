---
title: "2 Networks"
date: 2005-12-03
forum: General Help
---

### Post by k3nv on 2005-12-03
I have 2 interfaces, eth0 and eth1. I would like my ssh connections to go through eth1 and everything else to go through eth0. Is this possible?

eth0 = 192.168.2.x
eth1 = 192.168.0.x

I have ADSL coming into eth0 and cable internet coming into eth1. I want to download and browse with the internet with eth0. and use the internet connection from eth1 for ssh. Right now my default gateway is set to 192.168.2.1. But when I ssh through the eth0 side, it wants to send out through eth1.  Is there any way to have data that originates from one interface to go back out the same interface as well?

---

### Post by kosmic on 2005-12-03
Yes you can configure sshd to only listen to one interface in this case eth1

---

### Post by k3nv on 2005-12-03
Where would I set this option?  

Right now, when I ssh in through the ADSL side, since my default gateway is 192.168.2.1, it sends data out through eth1.

---

### Post by cylon359 on 2005-12-03
[QUOTE=k3nv]Where would I set this option?  

Right now, when I ssh in through the ADSL side, since my default gateway is 192.168.2.1, it sends data out through eth1.[/QUOTE]

You might have to use iptables/iproute2 to do this.  This is from memory, so it might not be correct...

Edit /etc/iproute2/rt_tables, and add a line for a new routing table (call it ssh or something).  ie:  You'll have the line:

200        ssh

Then, you can add a rule use this routing table for specially marked packets:

sudo ip rule add fwmark 1 table ssh

And add the route you want:

sudo ip route add default via 192.168.0.1 table ssh

Now, you want to modify the packets coming from SSH to go to that routing table:

sudo iptables -A OUTPUT -t mangle -p tcp --sport 22 -j MARK --set-mark 1

(I am not really sure about the iptables line though, again, because it's from memory), but what we are doing is saying that everypacket from port 22 (ssh) should have a mark of 1 set.  Then, all these packets will be routed out according to a different routing table which only has a route out your cable modem.

Hopefully that is of some use to you!  Stuff like this and more can be found at: [http://lartc.org/lartc](http://lartc.org/lartc)

---

### Post by gruepig on 2005-12-03
cylon359's reply looks good to me.

To see your network settings, you'll want to use the iproute tools: 'ip addr show', 'ip route show', 'ip rule show', and 'iptables -L' (or maybe 'iptables -t mangle -L').

Once you have your network working, you can add up lines to the appropriate stanzas /etc/network/interfaces (e.g., 'up ip route add default via 192.168.0.1 table ssh') so that when you bring your network interfaces up (which happens automatically on boot), everything will be set up.

---

### Post by k3nv on 2005-12-04
I can defintely chew on that for abit.  Thanks for the info.  I'll try it out.

---

### Post by k3nv on 2005-12-04
Hi,

I found this page is exactly what I needed to do:  [http://lartc.org/lartc#LARTC.RPDB.MULTIPLE-LINKS](http://lartc.org/lartc#LARTC.RPDB.MULTIPLE-LINKS)

Thanks for the link!

---

### Post by k3nv on 2005-12-04
hi again

where do I put the "ip route add" etc so it loads with these options at startup?

---

