---
title: "How to make iptables rule set permanent and on startup??please"
date: 2008-09-26
forum: General Help
---

### Post by spelman08 on 2008-09-26
I want to make this set of iptables rules permanent on startup
i run ubuntu hardy heron 8.04 LTS

```
sudo iptables -t nat -A POSTROUTING -o wlan0 -j MASQUERADE
sudo iptables -A FORWARD -i eth0 -j ACCEPT
sudo iptables -A FORWARD -i eth1 -j ACCEPT
sudo iptables -A FORWARD -m state --state ESTABLISHED,RELATED -j ACCEPT
echo 1 > /proc/sys/net/ipv4/ip_forward
```

Thanks in advance?

---

### Post by caljohnsmith on 2008-09-26
Try putting all those rules in your /etc/rc.local file, and you don't need to put "sudo" in front of the commands because the rc.local file gets executed as root. Give that a try and let me know how it goes.

---

### Post by Absorbed on 2008-09-26
This is might be a solution: [https://help.ubuntu.com/community/IptablesHowTo#Saving%20iptables](https://help.ubuntu.com/community/IptablesHowTo#Saving%20iptables)

---

### Post by crashdogy on 2013-04-30
> **caljohnsmith said:**
> Try putting all those rules in your /etc/rc.local file, and you don't need to put "sudo" in front of the commands because the rc.local file gets executed as root. Give that a try and let me know how it goes.


This work for me thanks

---

### Post by oldos2er on 2013-04-30
Old thread closed.

---

