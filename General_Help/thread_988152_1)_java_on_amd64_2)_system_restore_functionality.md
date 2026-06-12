---
title: "1) java on amd64 2) system restore functionality"
date: 2008-11-20
forum: General Help
---

### Post by jadhav333 on 2008-11-20
I have the following config on my machine.

[B]Quadcore intel cpu Q6600@2.4Ghz, 4 Gb ram
Ubuntu 8.10 Intrepid Ibex 64bit
_Partition Info:_
\-------------------Root------------10GB
\Home-----------Home----------10GB
\Media\Sda3---Data folder--400Gb[/B]

1) 64bit Ubuntu 8.10 is available only for amd64 architecture which actually works on a x86 architecture as well. 

This essentially displays my m/c as amd64bit. I am unable to access java based websites as sun java has not provided support for amd64 architecture.

I have tried installing openjdk, icedtea plugin, sun jre 6, ia32 sun jre, etc.. It gets installed. but I am not able to access the functionalities on my corp. network webmail which is based on sun java.

I req. the 64bit OS since I would like the speed benefit and also for full access to the 4GB RAM. My major applications are 3d based.

**question a** - How can I get access to java based  web functioanlity?
**question b** - Can I possibly get ubuntu64bit support for x86 architecture.

2) How can I create a 'system restore' kind of function where in I can create an image/snapshot of the state of the installations  at differrent points of time and can possibly restore those states in case I encounter any installation or softare related issues. 

The idea is to avoid the downtime if i ever have to re-install the system.

---

### Post by Nepherte on 2008-11-20
a) Remove the official sun java and install openjdk6 instead with the iceadtea-gcjwebplugin. Both can be installed through synaptic.

---

