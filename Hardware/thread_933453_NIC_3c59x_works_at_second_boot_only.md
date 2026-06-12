---
title: "NIC 3c59x works at second boot only"
date: 2008-09-29
forum: Hardware
---

### Post by StefanX on 2008-09-29
I have a PC with 3Com NIC which uses the 3c59x driver. Some weeks ago the system starts to act strange. The network connection is established after a second reboot only. This means after starting the computer the network manager icon shows that no network connection is established (icon with small orange triangle). Messages in /var/log/messages and /var/log/kern.log seems to be okay. I have to restart the system again (soft restart) and then the network is working without any problem. This problem is reproducible nearly 100%. 

Some time before the problem occurred that a network connection was established sometimes with 10mbit instead of 100mbit. 

I don't know if the problem is because of a defect NIC or how to investigate it further. Therefore any help is appreciated.

---

