---
title: "Winmodem issues AFTER the driver is installed :("
date: 2005-08-31
forum: Hardware &amp; Laptops
---

### Post by kate on 2005-08-31
I have installed the driver for my 536ep winmodem, and everything is going great supposedly...
I have dialup that I'm trying to make work, incase it helps.
I try to connect to the internet but this is what I get:
kate@ubuntu:~$ sudo pon
kate@ubuntu:~$ pppd
pppd: The remote system is required to authenticate itself
pppd: but I couldn't find any suitable secret (password) for it to use to do so.
pppd: (None of the available passwords would let it use an IP address.)

Anyone got any ideas? I'm a Linux newbie, remember, so try to keep it simple..

---

### Post by burlap on 2005-08-31
(Menu names may vary: I don't use English interface)

Open System log viewer (Applications -> System tools -> System Log). In the log viewer open file /var/log/messages and set monitoring mode ("Log" menu). 

Alternatively you can use terminal and run:
```
tail -f /var/log/messages
```

Open Network settings (System -> Administration -> Network settings) and set up your modem. Click "activate". Look in the log to see if it works. Later you may use modem-lights panel applet or gnome-ppp app to connect to the internet. Search the forums to find info on these apps or install via synaptic and try them out yourself.

---

