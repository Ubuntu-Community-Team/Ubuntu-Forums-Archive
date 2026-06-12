---
title: "Crossover cable?"
date: 2008-08-14
forum: General Help
---

### Post by cartisdm on 2008-08-14
I need to transfer some data from one laptop to another laptop.  I'm at a friend's house so my tools are limited and I'm trying to work on their computer.  I only have a straight through ethernet cable and I know that you need a crossover cable for PC to PC connections but my friend keeps telling me that the ethernet cards they use now can re-route the signal (or something like that) on their own now.

Can I network them together with just a simple straight through CAT5e cable?  My only other option is lots of transfers with my 2gb flash drive....](*,)

---

### Post by iaculallad on 2008-08-15
> **cartisdm said:**
> I need to transfer some data from one laptop to another laptop.  I'm at a friend's house so my tools are limited and I'm trying to work on their computer.  I only have a straight through ethernet cable and I know that you need a crossover cable for PC to PC connections but my friend keeps telling me that the ethernet cards they use now can re-route the signal (or something like that) on their own now.

Can I network them together with just a simple straight through CAT5e cable?  My only other option is lots of transfers with my 2gb flash drive....](*,)

No, you can't transfer data's between two similar devices using "straight-through" cable. You need to have a "crossover" type of cable.

:You could use your "straight-through" cable if you have a switch device around:

---

### Post by wilbbe01 on 2008-08-15
Ports are all pretty much auto sensing now, but iaculallad sounds confident in that a straight through won't work.  I connected 19 computers the other day to a network with crossover cables (straight through would have been the correct for that situation).  All machines worked fine, they automatically switched.  However I have no idea if machine to machine is smart enough to auto negotiate or not.  You could try it, I don't know if it would break anything or not.  Give each machine a static ip and see what happens.  No guarantees on your machine blowing up your house, or destroying its network card or anything though.

---

### Post by iaculallad on 2008-08-15
> **wilbbe01 said:**
> Ports are all pretty much auto sensing now, but iaculallad sounds confident in that a straight through won't work.  I connected 19 computers the other day to a network with crossover cables (straight through would have been the correct for that situation).  All machines worked fine, they automatically switched.  However I have no idea if machine to machine is smart enough to auto negotiate or not.  You could try it, I don't know if it would break anything or not.  Give each machine a static ip and see what happens.  No guarantees on your machine blowing up your house, or destroying its network card or anything though.

Switches nowadays are pretty much of auto-sensing so you could connect either straight-through or crossover cable to it. 

Newer version of Ethernet cards probably could support auto-sensing, but, I have not yet experienced or seen it.

---

### Post by y@w on 2008-08-15
Well.. you could spend a bunch of time trying to find out if your NIC is autosensing, or you could just plug it in, give them static IPs on the same subnet and try pinging :) A lot of newer NICs are autosensing. The good part is you only have to have the autosensing on one end.

---

### Post by wilbbe01 on 2008-08-15
> but, I have not yet experienced or seen it.

I googled and found one right away.  I assume a lot of modern computers do come with auto sensing ethernet.  I agree with yaw.  Why not just try it I don't think it would break anything.

---

### Post by jerome1232 on 2008-08-15
Isn't the worst thing that could happen is they start trying to send data on the same wire pair and it doesn't work?

---

### Post by y@w on 2008-08-15
Yeah, you won't break anything. I've done it hundreds of times (I used to configure PC-based firewalls for clients at work and use my Macbook to plug directly into them). The only thing to watch for is POE devices, but they have a different end on the cable.

---

### Post by wilbbe01 on 2008-08-15
I assumed nothing would happen, but I lost an ethernet card in a computer shortly after plugging in an incorrectly wired cable once, so I am sometimes not so quick on "just plugging it in," even though it was very much coincidental.

---

