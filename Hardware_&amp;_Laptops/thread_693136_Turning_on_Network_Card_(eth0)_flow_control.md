---
title: "Turning on Network Card (eth0) flow control?"
date: 2008-02-10
forum: Hardware &amp; Laptops
---

### Post by ph8 on 2008-02-10
Hey guys, can anyone tell me how to turn flow control on? I have a suspicion it's going to stop my (almost supported) network card from crashing regularly (usually when i put in huge amounts of traffic!)

---

### Post by Yellow Pasque on 2008-02-11
Use ethtool
 > ethtool -A|--pause DEVNAME      Set pause options
                [ autoneg on|off ]
                [ rx on|off ]
                [ tx on|off ]
e.g:
```
sudo ethtool -A eth0 autoneg on rx on tx on
```

---

