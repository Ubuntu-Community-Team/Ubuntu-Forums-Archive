---
title: "Kill The Process using terminal.."
date: 2009-06-03
forum: Installation &amp; Upgrades
---

### Post by mrridz on 2009-06-03
root@c0mrade-laptop:~/madwifi# airmon-ng start ath0


Found 5 processes that could cause trouble.
If airodump-ng, aireplay-ng or airtun-ng stops working after
a short period of time, you may want to kill (some of) them!

PID	Name
2678	NetworkManager
2696	wpa_supplicant
2701	avahi-daemon
2703	avahi-daemon
3268	dhclient
Process with PID 3268 (dhclient) is running on interface ath0


Interface	Chipset		Driver

wifi0		Atheros		madwifi-ng
ath0		Atheros		madwifi-ng VAP (parent: wifi0) (VAP cannot be put in monitor mode)

root@c0mrade-laptop:~/madwifi# 


im facing this problem while i trying to run airodump..can anyone tell me how to kill the process..?? need it a.s.a.p..
thanks..

---

### Post by spcwingo on 2009-06-03
Say, for example, you wanted to kill a process named wbar.  That would be:

```
pkill wbar
```

Or, if it's a process run by root:

```
sudo pkill wbar
```

---

### Post by Sub101 on 2009-06-03
Not sure of exactly your problem but to kill a process you can

```
pkill <processname>
or
kill <pid>
```

---

### Post by sehe on 2009-06-03
I don't really get the question. Here goes the generic answer

apropos kill
killall <processname>
man pgrep

/etc/init.d/avahi-daemon stop
/etc/init.d/wpa-ifupdown stop

luck

---

### Post by mrridz on 2009-06-03
thanks dude..ya'll bright my day..now i can use aircrack..thanks a lot..

---

