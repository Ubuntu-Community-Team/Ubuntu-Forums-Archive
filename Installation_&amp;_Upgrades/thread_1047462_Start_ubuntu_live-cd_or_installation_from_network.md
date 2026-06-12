---
title: "Start ubuntu live-cd or installation from network"
date: 2009-01-22
forum: Installation &amp; Upgrades
---

### Post by enli on 2009-01-22
Hi, I am a computer student and we have formed a Linux group in the college. I am one of the few who are using Linux for some time now and am responsible for the next session which will involve ubuntu installation with partitioning.

For the last 4-5 hours I have been trying to get ubuntu running from pxe boot. Not a single article worked for me, so I had to learn different things from different articles. Finally, I am able to network boot in Virtual Machine with Host networking but its a "command line" installation mode which we don`t want.

In short, our computer lab has around 30 computers where I am supposed to give students hands on demonstration of Ubuntu installation. I wonder if its possible to network boot ubuntu but in live-cd mode ?

After this session, I am going to try diskless ubuntu systems. Seems like there are plenty of guides for this but is it worth running 30 computers from central server?

Thanks
-EnLi

Update 1 : Found [https://wiki.ubuntu.com/LiveCDNetboot](https://wiki.ubuntu.com/LiveCDNetboot) but couldnt get it work either with intrepid. The CD boots, show verbose output but hangs at eth0 link up. Anybody has any clues ?

Update 2 : I booted with Hardy and Intrepid live-cds and it seems that it can not mount NFS share. If thats the case, how would wiki tutorial work?

---

### Post by enli on 2009-01-23
Bump.

The live-cd from the network doesnt go further 
eth0: link up
RPC : registered udp transport module.
RPC : registered tcp transport module.

Anyone?

---

### Post by tristangrimaux on 2009-07-19
I ran into the same problem. The nfs server was not accesible from the client. Now it's running fine!

---

