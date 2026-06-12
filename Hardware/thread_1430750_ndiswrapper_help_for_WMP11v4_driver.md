---
title: "ndiswrapper help for WMP11v4 driver"
date: 2010-03-15
forum: Hardware
---

### Post by tckotb on 2010-03-15
I've been having a lot of trouble with my wireless card, and ndiswrapper isn't helping at all. I installed all of the infs for the windows driver:
```
ndiswrapper -i wmp11nds.inf
```And blacklisted some other thing.
I also ran
```
ndiswrapper -m
```And I ran a lot of other commands, but it still won't work. 
Output of "iwlist scanning":
```
lo              Interface doesn't support scanning.

eth0          Interface doesn't support scanning.

vboxnet0   Interface doesn't support scanning.
```lspci:
```
...
03:03.0 Ethernet controller: Linksys, A division of Cisco Systems WMP11v4 802.11b PCI card
```
and "ndiswrapper -l" displays:
```
lsbcmnds : driver installed
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
lsipnds : driver installed
           device (17FE:2120) present
wmp11nds : driver installed
```

Should i run:
```

ndiswrapper -a 17FE:2120 lsipnds

```
It says it's risky...

---

