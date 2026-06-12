---
title: "Graphic card ubuntu-friendly for Gaming PC CPU Ryzen 7 2700"
date: 2019-03-29
forum: Hardware
---

### Post by GerryCM on 2019-03-29
Hello,


I'm building a PC gaming and by the moment, I have the CPU Ryzen 7 2700 and the motherboard MSI B450 Gaming Plus. I'm thinking to purchase 16gb 3200 ddr4 RAM. My question is this... Which is the best graphic card I would have to buy? Anyone could help me? I want to use it with free software drivers (I'm not closed to try with proprietary drivers), what I don't want is so much trouble with tricky configurations.



Many thanks for considering my request.


Gerard

---

### Post by Tadaen_Sylvermane on 2019-03-29
AMD open source drivers are getting quite decent. Don't know about Nvidia. But a linux box as a gaming machine... I love linux but I know that it is not a gaming OS by any means. Just not there yet, even with steam.

---

### Post by Autodave on 2019-03-29
I am running the exact system that you are building!  I do have 16G of ram.  I also have the Nvidia RTX 2070 8G graphics card.  I did have to add an additional PPA to get the newer driver for it, but other than that no hoops to jump through.  I will also agree with the above post that the AMD drivers generally work really well without any intervention.  (I am not sure about the Vega series, however.)  The Nvidia cards (1060, 1070, 1080) will work on the provided drivers in the repositories already installed.

---

### Post by GerryCM on 2019-03-29
Thank you all of you. I've finally bought Asus RX470 4gb for 90&#8364;, it's made for mining but the price is amazing. Maybe I'll change it in a few years but it's ok by now.

---

### Post by kurt18947 on 2019-03-31
> **Autodave said:**
> I am running the exact system that you are building!  I do have 16G of ram.  I also have the Nvidia RTX 2070 8G graphics card.  I did have to add an additional PPA to get the newer driver for it, but other than that no hoops to jump through.  I will also agree with the above post that the AMD drivers generally work really well without any intervention.  (I am not sure about the Vega series, however.)  The Nvidia cards (1060, 1070, 1080) will work on the provided drivers in the repositories already installed.

Vega was a problem, it would prevent machines using Ryzen processors with integrated GPUs (mine is a Ryzen3 2200G) booting. My experience is some months old, perhaps it's been fixed in the latest kernels, don't know. There was a fix on the bleeding edge at the time. I installed an older AMD PCIe video card as a quick fix. Not a gamer so performance isn't critical.

---

