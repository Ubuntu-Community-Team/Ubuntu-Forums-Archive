---
title: "No ethernet connection?"
date: 2012-02-28
forum: Hardware
---

### Post by PDA1 on 2012-02-28
I installed Lubuntu on my machine.

When I start Firefox there's no ethernet connection (wired).

ifconfig shows nothing but Lo and no mention of eth0 or any eth.

But....if I reboot the machine then I get an ethernet connection and can connect to the web with no trouble at  all.

Any ideas how to fix this?

---

### Post by PDA1 on 2012-02-28
Anybody?

---

### Post by dandnsmith on 2012-02-28
It sounds as if you're saying that you don't get the ethx interface when doing a 'cold' boot, but do when you do a 'warm' boot (ie a restart).
I've never had that failure mode - usually they either prove a bit intermittent during use, or they fail completely. I have one PC which has an eth interface on the motherboard - ifconfig shows it, but it has become useless (no packets will flow through it) (I had to add a separate interface card to get the machine working again).
I don't know how you sort your problem, but would be thinking about installing an additional card to get round it (they're not expensive)

---

### Post by PDA1 on 2012-02-28
On a notebook?  I trash picked the thing so I'm not investing anything into it.

When running Ubuntu 11.04 the ethernet connection is fine.  But, in 11.04 with a super slow computer it's a pain to use so I switched to Xfce/Lubuntu

---

### Post by dandnsmith on 2012-02-29
"On a notebook?" - one of those little details, which mean so much - as also is the release number of the distro and any comparative anomalies (as you finally disclosed).

What you are really saying then is that you have differences in the hardware shown by different OS versions.

You could try Mint11 - that I've found better than Ubuntu11.04 - or one of the lighter weight distros, or one of the older Ubuntu releases.
There is always an element of choice to be balanced against personal preferences and perceived speed, especially for somewhat older hardware.

---

### Post by Rodney9 on 2012-02-29
This may help - 
[https://help.ubuntu.com/10.04/serverguide/C/network-configuration.html](https://help.ubuntu.com/10.04/serverguide/C/network-configuration.html)


For How-To's, Information and Screen-Casts on Lubuntu go to the
Lubuntu One Stop Thread - 

[[COLOR="Blue"]Lubuntu One Stop Thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1844755")

Rodney

---

