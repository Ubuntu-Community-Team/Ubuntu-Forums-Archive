---
title: "Linksys PCMCIA on HP N3310"
date: 2006-02-17
forum: Hardware &amp; Laptops
---

### Post by Cedfelix on 2006-02-17
I'm pretty new to linux and having a hard time getting my network card up and running on my machine. It's plugged in and all the lights are on, but i'm not connecting to the network. What can I do? Any suggestions? I really appreciate all the help.

---

### Post by Cedfelix on 2006-02-17
Okay, maybe this info will help.

```
ifup eth0
ignoring uknown interface eth0=eth0
```

Also, "ifconfig" only shows "lo", not "lo" and "eth0"

---

### Post by K.Mandla on 2006-02-17
There are some very good suggestions here; have you seen them yet?

[https://wiki.ubuntu.com/UserDocumentation#head-2167d6cc9b218b20c4e1a883d65101c212f19a12](https://wiki.ubuntu.com/UserDocumentation#head-2167d6cc9b218b20c4e1a883d65101c212f19a12)

And could you tell us a little more about your computer and network card? It's possible you need to install ndiswrapper to get things started.

---

### Post by Cedfelix on 2006-02-17
Okay, the network card is a Linksys PCMPC100 v2 wired network card, the laptop is a HP Pavilion N3310 AMD K6 500Mgz 128Mb RAM, 4gb hd. Any other info?

---

### Post by Cedfelix on 2006-02-17
turns out i had to sudo kcontol and set my eth0 to dhcp and then restart my networking. thanks for the informational link though. later.

---

