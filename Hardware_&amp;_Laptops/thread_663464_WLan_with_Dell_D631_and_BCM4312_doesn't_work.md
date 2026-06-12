---
title: "WLan with Dell D631 and BCM4312 doesn't work"
date: 2008-01-10
forum: Hardware &amp; Laptops
---

### Post by gogi on 2008-01-10
Hi all!

I've got a brand new Dell Latitude D631 notebook. Now everythink works fine but wlan.

My problem IS NOT module loading or similar stuff. A command like "iwlist eth1 scan" works fine and my networkmanager also shows available networks.

But what's not fine is: The D631 can't get into my network. Doesn't matter if wpa or wpa2.

I've played with bios setting due to a switch on the notebook side called "wi-fi catcher" but it doesn't help.

Any ideas?


```
lspci | grep BCM 4312
0b:00.0 Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 01)
```

Module bcm43xx is loaded and firmware is installed too.


Thanks

Gogi

---

### Post by lank23 on 2008-02-06
I have a D620 that is working fine and I am using wpa2 with a d-link router.

post  lspci and lsmod

lank23

---

### Post by slayer^_^ on 2008-04-25
don't use bcm43xx , use ndiswrapper... if you've got a (rev 01) bcm4312 it should work without patching your kernel...


here's how yo ucan do it

[http://ubuntuforums.org/showthread.php?t=659027](http://ubuntuforums.org/showthread.php?t=659027)

good luck :)

---

