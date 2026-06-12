---
title: "installing ubuntu with etherboot"
date: 2006-01-30
forum: Installation &amp; Upgrades
---

### Post by Droopy on 2006-01-30
Can some help me?
i want to install ubuntu over the network with etherboot but i don't know where to begin!! 

Etherboot is a software package for creating ROM images that can download code over an Ethernet network to be executed on an x86 computer. Many network adapters have a socket where a ROM chip can be installed. Etherboot is code that can be put in such a ROM. Etherboot is normally used for for booting PCs diskless. This is useful in various situations, for example:

An X-terminal. 
Clusters of compute servers. 
Routers. 
Various kinds of remote servers, e.g. a tape drive server that can be 
accessed with the RMT protocol. 
Machines doing tasks in environments unfriendly to disks. 
A user platform where remote partitions are mounted over the network 
and you are willing to accept the lower speed compared to disk. 
Maintaining software for a cluster of equally configured workstations 
centrally. 

Etherboot can boot computers faster than from a disk because there are no delays in spinning up disks, etc. A moment's calculation will show that even with a 10Mbit Ethernet, sending a 500kB kernel will take only a couple of seconds typically. With 100Mbit Ethernet it gets even better.

---

