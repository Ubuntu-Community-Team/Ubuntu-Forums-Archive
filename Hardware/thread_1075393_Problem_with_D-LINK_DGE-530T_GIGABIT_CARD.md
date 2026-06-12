---
title: "Problem with D-LINK DGE-530T GIGABIT CARD"
date: 2009-02-20
forum: Hardware
---

### Post by garton on 2009-02-20
I have a 8.04 (LTS) installation that I recently installed a D-link DGE-530T PCI card into. Works out of the box... for a while. An hour or so after booting the maching, the NIC stops working. Just plain stops, nothing in dmesg and nothing in /var/log/messages about anything wrong.

If I do "dhclient eth1", it re-fetches the IP from the DHCP server and goes back to normal.

What could be the problem here? Should I install the drivers from the CD that shipped with the card?

---

### Post by Teh_Messiah on 2009-03-16
Hi,
I was curious if you resolved this issue?
I need to buy a gigabit NIC for my file server which runs Xubuntu 8.10.
I dont want to buy anything that isnt going to work.
My server has a static IP address so its easier to get to from my other computers to transfer data.
Have you tried setting a static address?
Regards Ben

---

### Post by garton on 2009-05-09
Nope, it's still the same.

No, I have not tried setting a static IP.

---

### Post by fermulator on 2010-11-05
Having this problem with static IP....

Ubuntu Server 10.04
D-Link DGE-530T

After some amount of time, the network just stops working, and I have to issue:```

sudo ifdown eth0
sudo ifup eth0
```

NOTE:  I can make the problem happen REALLY QUICK if I try to scp some huge file from some other server to this box w/ the D-link card in it.....

---

### Post by bobnn on 2010-12-11
Any news on this?  I'd like to use this card on 10.04.1 LTS, as it does Gigabit and comes with half height brackets, but if it can;t stand the traffic it will be useless to me.

---

