---
title: "Compaq Laptop Wi-Fi detects network, doesn't connect."
date: 2007-10-21
forum: Hardware &amp; Laptops
---

### Post by pyromaster114 on 2007-10-21
I installed Kubuntu on my Compaq Laptop, and everything works great except one thing:
The wireless doesn't connect. It sees the wireless networks, but when I try to connect, it doesn't connect. (usually)
The strange thing is, it works like 5% of the time. I've gottent it to connect once or twice by doing this:

sudo vim /etc/network/interfaces

putting in under the eth1:
wireless-essid MYSSID
wireless-key MYWEPKEYHERE

then saving that file, and typing

sudo ifdown eth1
sudo ifup eth1

Then, sometimes it connects, but only about 5% of the time.

I don't understand what I'm doing wrong, because i'm relatively close to teh access point/router, if it were a driver problem I'd think it wouldn't work at all...

EDIT: New problem.
I can connect to one wireless network per time I restart.
That is, if I wanted to change wireless networks, I'd have to restart the computer.

---

### Post by Mimsy on 2007-10-22
Similar problem here, with Ubuntu Feisty on a Compaq nc6220. I can see the wireless adapter, and when I applied the above fix above by editing /etc/network/interfaces, and then typing 
sudo ifdown eth1and sudo ifup eth1 lets me connect, *if* I reboot the laptop. When it restarts, I can connect, but it is not a long-time connection.

I am typing in the nc6220 now, and I hope it stay online long enough to let me post :)

---

