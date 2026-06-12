---
title: "problems with networking while using the integrated networking on my mobo"
date: 2007-02-26
forum: Hardware &amp; Laptops
---

### Post by mm144 on 2007-02-26
my full system specs if it matters:
intel core 2 duo 6700
4gb ram
2geforce 8800  gtx
ECS PN2 SLI2+ (680i SLI) Motherboard
(just built)

i've got feisty fawn herd 4 installed
the installation went well
but once i finished i noticed my networking was not functioning 

the motherboard has two ethernet ports 
only the first one is being used (eth0) the other one has no cable attached
it seems to have detected the driver correctly (however i'm uncertain of this)
a bubble comes up as soon as i log in saying that it has connected to a wired network
but all it seems to do is connect itself to the loopback network 127.0.0.1
does anybody have any ideas?
ok under further inspection of the problem i can add some info:
one: it is using the forcedeth driver
and 
two: it seems to be stuck trying to connect to ipv6 network where only ipv4 exists in which i don't know how to fix this

---

### Post by Mcavity on 2007-11-05
this might help

[http://ubuntuforums.org/archive/index.php/t-87798.html](http://ubuntuforums.org/archive/index.php/t-87798.html)

---

