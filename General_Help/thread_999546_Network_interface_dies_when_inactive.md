---
title: "Network interface dies when inactive"
date: 2008-12-02
forum: General Help
---

### Post by martinpg on 2008-12-02
Hi, I have a problem with my installation of Ubuntu server 8.0.4 as follows. I have two machines, machine 1 and 2 and I have a KVM switch to enable me to switch between them as needed. Ubuntu server is running on machine 1. If I leave the KVM switch pointing to machine 2 and don't access machine 1 for about twenty minutes or so, then it stops responding to network pings and other accesses such as http and samba.

If I switch the KVM switch over to machine1, the screen is blank and so I hit Enter, and then I can hear the machine whirring up into action. It looks as though the machine goes into some sleep mode and needs to be actively woken up, but the fact that the network connections go to sleep too is a problem.

Does anyone know how to prevent the machine going to sleep like this? Thanks, Martin

---

### Post by martinpg on 2008-12-09
Hi - just in case anyone encounters this same problem, here's what I did to solve this. I added apci=off to the relevant kernel line of the grub menu.lst file. Then I rebooted and the system now keeps its network connectivity just fine.

Actually, I believe that this fix just ensures that the system never goes into any sort of sleep mode, and so it may not be the right fix, but at least it solves my immediate problem.

---

