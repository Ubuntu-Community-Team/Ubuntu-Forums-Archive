---
title: "rename eth1 to eth0 (replaced NIC after install)"
date: 2008-12-10
forum: Hardware
---

### Post by jeffk on 2008-12-10
What is the mechanism for permanently renaming an interface in Ubuntu 8.10 Intrepid?

I had a dodgy 8139too (module) based NIC installed at startup. I switched that out for a unit that (apparently) uses 8139cp. At any rate the point is that the new NIC is eth1, and I'd like to switch it permanently back to eth0 to be consistent with the other Ubuntu systems I manage.
```
/etc$ sudo grep -R eth1 *
modprobe.d/blacklist:blacklist eth1394
network/interfaces:auto eth1
network/interfaces:iface eth1 inet static
udev/rules.d/70-persistent-net.rules:
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="(snip)", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"
```
Do I only need to change the 70-persistent-net.rules and network/interfaces, then reboot?

---

### Post by Shots on 2008-12-22
Hi,

Just edit udev/rules.d/70-persistent-net.rules end set if number to correct mac address.

Shots.

---

### Post by usererror on 2009-05-06
> **Shots said:**
> Hi,

Just edit udev/rules.d/70-persistent-net.rules end set if number to correct mac address.

Shots.

That worked for me!  Thanks! the other place /etc/iftab/ doesn't exist anymore it seems.

---

### Post by fro1269 on 2011-03-09
> **Shots said:**
> Hi,

Just edit udev/rules.d/70-persistent-net.rules end set if number to correct mac address.

Shots.

what do you mean by "end set if number to correct mac address."?

---

### Post by iissmart on 2011-05-09
> **fro1269 said:**
> what do you mean by "end set if number to correct mac address."?
Match the MAC Address to the device name is what they mean.

---

### Post by ub-newbie on 2013-04-06
Update for those who search.
on 12.04 server & 10.04 desktop (and probably others) you want to look in /etc/udev/rules.d/

---

### Post by Iowan on 2013-04-06
From the Code of Conduct:
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

