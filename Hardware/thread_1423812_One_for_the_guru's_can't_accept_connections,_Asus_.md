---
title: "One for the guru's: can't accept connections, Asus M2NPV-VM MCP51 Ethernet forcedeth"
date: 2010-03-07
forum: Hardware
---

### Post by tyn on 2010-03-07
Now this one really has me stumped.  I sure hope someone can lend a hand.

I have an ASUS M2NPV-VM motherboard which uses Nvidia's MCP51 for its ethernet (eth1).  I am running Ubuntu 9.10 (kernel 2.6.31-19-generic SMP).  I have Mediatomb, ssh and samba servers running; iptables is in its default (let everything in/out) state.

When I connect to my local network I can ping it from other machines and access the network from it but I cannot make a connection to it e.g. ssh gives a timeout error.  I have a PCI network card (eth2) installed and when I connect it to the network everything works fine.  Note: both eth1 and eth2 are configured with the same IP address, but only one ever has an Ethernet cable connected to it.

It looks like all the server software is configured correctly but the inbuilt eth1 is only partially working: will do everything except accept connections.

I tried removing and reinstalling forcedeth (sudo rmmod forcedeth; sudo modprobe forcedeth) but it didn't help.

Can anyone give me some advice on this one?

Thanks,
Ty

---

### Post by tyn on 2010-03-10
Ah, I thought this one would stump everyone.  It is very strange system behaviour.  I am going to try a memory stick install of 9.04 and see if the onboard ethernet works with that version.

---

### Post by tyn on 2010-03-10
Well, well.  It didn't take very long to get Xubuntu 9.04 (AMD64 build) up and running.  Interestingly enough the ssh server worked instantly.  I guess this means that the hardware works.  There must be something wrong with my Ubuntu 9.10 (x86 build) installation.  It could also be a recent driver problem; I have not updated any of the packages in my Xubuntu install yet.

---

