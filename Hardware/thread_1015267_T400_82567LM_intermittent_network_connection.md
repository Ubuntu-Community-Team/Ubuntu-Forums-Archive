---
title: "T400 82567LM intermittent network connection"
date: 2008-12-18
forum: Hardware
---

### Post by shinew on 2008-12-18
Hello, I just installed Ubuntu 8.10 Intrepid 64-bit on my T400, everything is working "out of the box", except that my LAN connection stalls every few minutes. 
So every few min, my connection(WIRED) will just stop responding for around 20 seconds or so. The network does not display as "disconnected", it just stalls. This is really annoying especially I'm using it as a synergy client.

anyone has experienced similar problem? is this a driver thing or I just need to tweak some settings? any help is appreciated. thanks!!


###################SOLVED##################
it tuned out not to be my laptop's fault. It was my TRENDNet Gigabit router. After I did a factory reset, all is good! I can't believed I wasted all day on that...

---

### Post by shinew on 2008-12-19
bump

---

### Post by IQRules on 2008-12-19
Can you post "$ lspci | grep -i network" ? How about the /etc/network/interface file?

---

### Post by shinew on 2008-12-19
here it is:
```
00:19.0 Ethernet controller: Intel Corporation 82567LM Gigabit Network Connection (rev 03)
03:00.0 Network controller: Intel Corporation PRO/Wireless 5100 AGN [Shiloh] Network Connection

```

I've made some progress. I downloaded the newer e1000e driver v0.5.8.2-NAPI & loaded it(my old one is 0.3.3.3-k6). It might have fixed the problem but I haven't used it long enough to verify this yet. However, the problem is that I don't know how to load it on boot. So every time when it reboots, it goes back to 0.3.3.3-k6. should I just add a line in the "/etc/modules" file? if so, what should I add? 

thanks alot!

---

### Post by shinew on 2008-12-20
bump!

---

