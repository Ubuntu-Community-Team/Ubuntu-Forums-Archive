---
title: "Unstable Internet Connection in UBUNTU"
date: 2007-09-29
forum: Hardware &amp; Laptops
---

### Post by sou.1234321 on 2007-09-29
My [COLOR="Red"]**[SIZE="4"]Internet connection is not remaining stable/consistent[/SIZE]**[/COLOR].

It's coming -> then going away -> then again coming. It's behaving on its own!!!

Everytime I am trying to update the UBUNTU, it's failing due to the unstable connection.

I am getting fed up everytime. Again starting the update, but again with same fate.... 

PLEASE HELP me out..... :(

(I have Attansic Ethernet L2 Fast Ethernet Card with a dsl broadband connection)

---

### Post by jcliburn on 2007-09-30
Immediately following a network dropout, please open a terminal window and execute these commands.

```
sudo ethtool -S eth0 > ~/ethtool-s.txt
sudo grep -i atl2 /var/log/messages > ~/var-log-msg.txt
```

The output of the commands will be saved to files in your home directory.  After your connection comes back up, post the contents of those files here.

---

