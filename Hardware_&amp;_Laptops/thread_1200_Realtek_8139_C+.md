---
title: "Realtek 8139 C+"
date: 2004-10-19
forum: Hardware &amp; Laptops
---

### Post by retrakker on 2004-10-19
Both modules 8139cp and 8139too get loaded upon start but no device (eth2 in my case as eth1 is the wireless card). rmmod'ing either one does not help (also with restarting /etc/init.d/networking). I tried to figure out to disable either one, no clue? 

Which daemon is doing the hardware detection, where I can read manuals about that?

---

### Post by retrakker on 2004-10-20
Answering myself:

the place is /etc/hotplug/blacklist

```

# causes problem with other realtek driver &#40;8139cp&#41;
8139too

```

Apparently the connection has a long delay, need to figure out what is that all about.

---

### Post by oddabe19 on 2004-10-21
[quote=retrakker]Answering myself:

the place is /etc/hotplug/blacklist

```

# causes problem with other realtek driver &#40;8139cp&#41;
8139too

```

Apparently the connection has a long delay, need to figure out what is that all about.[/quote]

I have that long delay problem too... how did you fix it?

---

