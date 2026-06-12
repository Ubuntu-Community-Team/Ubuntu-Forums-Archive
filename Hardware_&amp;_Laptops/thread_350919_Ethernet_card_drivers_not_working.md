---
title: "Ethernet card drivers not working"
date: 2007-02-01
forum: Hardware &amp; Laptops
---

### Post by simon303 on 2007-02-01
After I installed Ubuntu 6.10 Edgy my ethernet card stopped working
It is a Belkin card based on the Realtek RTL8139 chipset
The drivers exist on the system and are 8139too but the system does not recognise the card
Is there anyway of 'reminding' the system the drivers exist and where the drivers are?
Thanks

---

### Post by JamieC on 2007-02-01
How did you install the drivers? Open a new terminal window (Applications -> Accessories -> Terminal) and post the output of the following commands:-

```

lspci

```

```

ndiswrapper -l

```

```

iwconfig

```

---

### Post by simon303 on 2007-02-02
i will do that as soon as i get home.
i didn't actually install the drivers, they come with ubuntu and apparently ubuntu auto-detects the card, but it hasn't happened

---

