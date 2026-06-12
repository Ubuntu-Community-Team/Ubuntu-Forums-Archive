---
title: "eeebuntu drivers"
date: 2009-01-26
forum: Installation &amp; Upgrades
---

### Post by clark333 on 2009-01-26
Hi there -

I've installed Eeebuntu on my Advent 4211C netbook - which is running superb and i love this Linux version, however:-

I cant get my wireless connection which I think is due to no drivers being detected. (as have "?" next to my CPU, Host and VGA controller, SCSI device, ethernet controller, WLan interface).

Any ideas how I could get these drivers installed?

---

### Post by snowpine on 2009-01-26
Eeebuntu is designed for the Asus eee pc and uses a special eeepc kernel designed specifically for that machine.

Have you ever tried "regular" Ubuntu on your Advent netbook? If "regular" Ubuntu works okay, but you like eeebuntu better, my recommendation is to install the generic linux kernel. You can do this in Synaptic by searching for linux-generic.

Good luck!

---

### Post by clark333 on 2009-01-26
Im sure eeebuntu is for netbooks and not just specifically for asus ee pcs. maybe your right though, could try and install ubuntu on it instead.

---

### Post by snowpine on 2009-01-26
You don't necessarily have to install Linux distros to see if they work on your hardware. You can test them from a Live CD or USB thumb drive first. Just a little tip to save you some time. :)

From the eeebuntu website:

"Can I Install Eeebuntu On Another Netbook I.E. Not An EeePC?

The strength of Eeebuntu lies in its custom kernel and the Eeeconfigure system which, at the moment, has no provision for other netbooks. However since the Eeeconfigure system is extensible and many of the kernel modifications are designed for generic components (i.e. different wifi cards) there is a strong chance that the install will work out of the box and then you can record your own scripting modifications with Eeeconfigure, then share them with the community so they too can install on their netbooks.
We have had feedback that in addition to the EeePC range of netbooks, Eeebuntu also runs out of the box on: the Eee Box, the Acer Aspire One, the Samsung NC10."

I am not familiar with the Advent netbook; what OS did it come pre-installed with?

---

### Post by piousp on 2009-01-26
I cant check it right now, but there should be a script where it "installs" the eeepc's wireless dirvers.

---

### Post by snowpine on 2009-01-26
I am 100% certain eeebuntu uses the eeepc kernel from array.org. This special kernel has built-in eee pc wireless support, therefore additional drivers are not necessary.

(edit) It also includes the eeeconfigure script to further customize other features of your specific eee model, that's what you may be thinking of.

---

### Post by clark333 on 2009-01-26
Hi - 

I got this fixed by reinstalling eebuntu from my flashpen, it seemed to detect my wireless router right after install, all i needed to do was type in my WEP and hey presto.  I can surf away on linux eebuntu (which is practically ubuntu 8.10) until my hearts content!  So, i dont know what the origial fault was but its working now

---

### Post by piousp on 2009-01-27
Nice to hear that!
Maybe you can mark this thread as SOLVED ;)

---

