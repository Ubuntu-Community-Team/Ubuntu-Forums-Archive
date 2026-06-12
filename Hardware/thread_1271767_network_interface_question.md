---
title: "network interface question"
date: 2009-09-21
forum: Hardware
---

### Post by faustot on 2009-09-21
I just started using ubuntu and i have some passing linux knowledge (not too much)

i had a problem where my internet connection was very slow. after some research on these forums i was able to find that it was running at 10M half duplex and i was only getting a 1300 kbps downstream after running:

sudo mii-tool eth0 --force=100baseTx-FD

that corrected the probelm and i'm now getting 35000 kbps downstream. the problem i'm having is that when i reboot the computer, it reverts back tot he old settings.

what would be the way to keep these settings even through reboot ?

---

### Post by SteveDee on 2009-09-21
I suggest you try ethtool. I can't remember if its part of the standard install, so go System > Administrator > Synaptic Package Manager and install if necessary.

At a terminal:-
man ethtool {for info}
sudo ethtool ethx {where x is your network number, which you can get from "ifconfig". This shows network details}

...and something like:-
sudo ethtool -s ethx speed 100... {to set it}

Good luck!

---

### Post by faustot on 2009-09-21
i tried ethtool, i was able to get it to make the the speed 100 but no matter what i did i can't get it to be full duplex

when i tried mii again, it worked like a charm .. but it stops working every reboot

---

### Post by SteveDee on 2009-09-22
> **faustot said:**
> i tried ethtool, i was able to get it to make the the speed 100 but no matter what i did i can't get it to be full duplex

when i tried mii again, it worked like a charm .. but it stops working every reboot

I guess we need to workout where the network adapter settings are stored.

I have a similar situation with "wakeup on lan" and simply run a script automatically every time 'buntu loads to re-establish my required settings. Maybe you could do the same as a short term solution until you can fix this properly?

---

