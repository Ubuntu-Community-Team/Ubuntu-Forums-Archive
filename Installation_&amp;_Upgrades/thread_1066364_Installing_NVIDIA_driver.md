---
title: "Installing NVIDIA driver"
date: 2009-02-10
forum: Installation &amp; Upgrades
---

### Post by PhoenixDream on 2009-02-10
Im having trouble installing the latest drivers for my 9600GT card.

What I have done so far:

Checked for hardware drivers thru System>Admin>Hardware Drivers, nothing there.

Downloaded the latest driver from nvidia and tried to install it using:
sh NVIDIA-linux-x86-180.22-pkg1.run
 it then gave me error 'needs root privilege' so I try:

benny@bennybuntu:~/Desktop$ sudo sh NVIDIA-linux-x86-180.22-pkg1.run
[sudo] password for benny: 
sh: Can't open NVIDIA-linux-x86-180.22-pkg1.run
benny@bennybuntu:~/Desktop$ 

and thats what I get....
Ive tried reading numerous posts but I cant come to anything conclusive.
Is there something I may have missed?:confused:

Any help would be appreciated.

---

### Post by taurus on 2009-02-10
Did you save NVIDIA-linux-x86-180.22-pkg1.run to your desktop?

```
cd ~/Desktop
ls -la
```
Another way is to install envy from synaptic and use it to install nvidia driver for your graphic card unless you really want to install it by hand.

---

### Post by PhoenixDream on 2009-02-11
Hi Taurus,

Yes I saved it to my desktop, but I ended up actually upgrading from 8.04 to 8.10 (sorry I forgot to mention which version of ubuntu I was using).

I was able to activate the nvidia driver via System>Admin etc.

Though I appreciate your response and help nevertheless! :)

---

