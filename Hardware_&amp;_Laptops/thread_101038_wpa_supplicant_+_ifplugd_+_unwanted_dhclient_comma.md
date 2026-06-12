---
title: "wpa_supplicant + ifplugd + unwanted dhclient command"
date: 2005-12-08
forum: Hardware &amp; Laptops
---

### Post by cheeseballs on 2005-12-08
Using a cl56 laptop
Wireless switch set to on
wpa_supplicant is configured and using default startup scripts that install with package.

ifplugstatus shows link beat detected on eth1
eth1 is using ipw2200

Wired networking is perfect with ifplug
Wireless network requires manually running dhclient eth1. Picks up ip address in less than a second from dhcp server everything runs fine afterwards.

I would like the wireless card to automatically pick up a ip address when the toggle switch is set to on. Just like the wired ethernet picks up an address when it is plugged in.

Toggling the wireless switch on/off multiple times does not fix the problem.
Any suggestions?

---

### Post by ketilkn on 2005-12-10
double post

---

### Post by ketilkn on 2005-12-10
Do you have the line 
 ```
 iface eth1 inet dhcp
```

in your /etc/network/interfaces  ?

If not, what does you /var/log/syslog say when you flick the switch?

---

