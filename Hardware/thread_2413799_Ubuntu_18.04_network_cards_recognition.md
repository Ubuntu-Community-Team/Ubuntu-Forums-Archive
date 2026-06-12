---
title: "Ubuntu 18.04 network cards recognition"
date: 2019-03-02
forum: Hardware
---

### Post by francofienga on 2019-03-02
Hello everyone,
since I installed Ubuntu 18.04 on my desktop PC (previously I had Ubuntu 14.04 and everything worked properly) the 1 Gbit/s network card is not identified as eth1 but as eno1 and, more seriously, it works at 100 Mbit/s.
Until now I have neglected the thing; but since I am about to receive 1 gigabit Internet connectivity, now I need to solve this anomaly.
Grateful to anyone who can help me to solve.

---

### Post by kc1di on 2019-03-02
Hello francofienga and Welcome to Ubuntu Forums,

First thing will be to determine which card your talking about and which driver is being used.
go to a terminal and type this command and post the output here ```
inxi -Nn
```
Inxi may not be install if it's not install it first with this command ```
sudo apt install inxi
```

---

### Post by SeijiSensei on 2019-03-02
What about any switches or routers in use? Do they have GigE Ethernet?

---

### Post by francofienga on 2019-03-03
Thanks for your support.

```
francesco@francesco-i7:~$ inxi -NnNetwork:   Card: Intel 82579V Gigabit Network Connection driver: e1000e
           IF: eno1 state: up speed: 100 Mbps duplex: full mac: 30:85:a9:95:19:7a
francesco@francesco-i7:~$ 



```

---

### Post by francofienga on 2019-03-06
There are no switches and the router has a GigE port.
Thanks anyway.

---

