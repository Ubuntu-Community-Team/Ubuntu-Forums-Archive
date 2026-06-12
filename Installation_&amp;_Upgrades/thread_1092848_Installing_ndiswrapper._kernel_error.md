---
title: "Installing ndiswrapper. kernel error"
date: 2009-03-10
forum: Installation &amp; Upgrades
---

### Post by rowebil on 2009-03-10
Using Debian

I'm trying to install ndiswrapper.

I had to install the build-essentials.

I did. It worked.

Im using the root account on terminal. 

I extracted the file from CD to /home/billy/Desktop/ndis
question #1, If I delete that off of my desktop, will it screw up ndis? I couldn't put it in /usr/src/ because it kept saying restricted.. 

I typed 
cd /home/billy/Desktop/ndis
make


It said 
-C driver install
entering directory /home/billy/Desktop/ndis/driver'
makefile:34: *** cannot find kernel version in /lib/modules/2.6.26-1-686/build, is it configured? Stop!
Leaving directory
install error 2


Question 2, can someone tell me what went wrong? And what to do?
Please help!

---

