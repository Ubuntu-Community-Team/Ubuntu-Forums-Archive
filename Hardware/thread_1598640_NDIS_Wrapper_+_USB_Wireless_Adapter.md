---
title: "NDIS Wrapper + USB Wireless Adapter"
date: 2010-10-16
forum: Hardware
---

### Post by ki4jgt on 2010-10-16
Bus 001 Device 003: ID 0457:0163 Silicon Integrated Systems Corp. 802.11 Wireless LAN Adapter

Will it work with NDISWrapper? I have tried plugging it in directly. Doesn't work!

Made by EDUP

---

### Post by silbak04 on 2010-10-16
I suggest you install the attachment that I have attached. Install in the right order, because each file depends on the other. To do this just open up a terminal (Applications->Accessories->Terminal) and type this:

```

$ tar -zxvf file.tar.gz

```

Once this is done, go to System->Administration and you should see something like Windows Wireless drivers. Click on that and once that opens up, you're going to need to click on Install New Driver. You're going to need to browse for the .inf file of your wireless adapter...usually if you have the cd for your adapter, you can just pop in the cd, and browse for .inf file within the cd.

I hope this helps!

---

### Post by ki4jgt on 2010-10-16
Thanks

---

