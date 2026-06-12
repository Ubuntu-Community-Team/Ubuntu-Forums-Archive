---
title: "Wireless connection gets lost"
date: 2005-11-03
forum: General Help
---

### Post by Unenvarjo on 2005-11-03
Hello,

I'm having some trouble with my wireless connection (as the topic says). I have tested this problem on two different machines, a pretty standard AMD Duron machine and a Asus Pundit-R book-sized machine. The Pundit-R uses Orinoco Silver PCMCIA card for network connection, the "standard pc" uses A-Link WL54USB. They are both connected to a Buffalo Airstation and both use Ubuntu Breezy.
Right after boot, the connection works fine for a while, from one hour to a couple of days. Then the trouble starts. First the traffic gets funny (duplicate packages clogging the traffic, packet loss), then the connection to the AP is completely lost. The Pundit-R worked just fine using hoary and before that with Gentoo (but I got tired of the endless compiling).

Any ideas how to fix this? I get a normal network connection by rebooting or switching the USB stick to my Pundit-R and setting this as the default gateway to the "standard pc" or vice versa.

---

### Post by MarcDM on 2005-11-03
Hey Unenvarjo,
try this and see if it helps your problem :
[http://ubuntuforums.org/showthread.php?t=85193]("http://ubuntuforums.org/showthread.php?t=85193")
I experienced similar problems using certaim dhcp servers. 

It happened especially when I was unable to renew a lease so the netwok adapter went into some strange kind of sleep mode.

---

### Post by Unenvarjo on 2005-11-04
Thanks MarcDM,

that might be the case. I'll see if this helps.

---

