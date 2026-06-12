---
title: "How to  Ubuntu LTSP server and Thin clients"
date: 2009-06-25
forum: Installation &amp; Upgrades
---

### Post by alejobar on 2009-06-25
--------------------------------------------------------------------------------

Hi there, I'm trying to have a network with one Ubuntu 8.04 LTSP server and 2 thin clients. I already install the LTSP server following this instructions: [https://help.ubuntu.com/community/Ub...SPQuickInstall](https://help.ubuntu.com/community/Ub...SPQuickInstall)

At the end it said that it will be ready to boot the first thin client.... well how???

The computer that I'm testing have 2 network cards, and both where recognize it at the installation, I choose one to be the acces to the internet. After finishing the installation I connecta a second pc to the other ethernet port, boot the second pc and in set up change to the first boot the network card, save and close, reboot and nothing 

Could someone please please please help me to do this setup?

---

### Post by smaclean on 2009-06-26
If you are connecting the pc that you want to use as the thin client, directly to the 2nd nic card of the ltsp pc, without using a hub or switch, you need to use a crossover cable.

---

### Post by alejobar on 2009-06-26
it worked!!!! I just need to use a switch, dumb me!. Now my thin client its working ok, I just have a question, how can I change the resolution?. I can only use 640x480, since I using a KVM to share the screen and keyboard do you think that could be the problem?

---

