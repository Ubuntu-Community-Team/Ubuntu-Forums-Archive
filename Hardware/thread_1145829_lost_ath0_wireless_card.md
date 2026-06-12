---
title: "lost ath0 wireless card"
date: 2009-05-02
forum: Hardware
---

### Post by macabro22 on 2009-05-02
Please help me find out why my wireless connection suddenly disappeared.

I found a suspicious part of kernel.log:
```

May  2 01:50:07 Watilla kernel: [   14.778186] lp: driver loaded but no devices found
May  2 01:50:07 Watilla kernel: [   14.810013] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
May  2 01:50:07 Watilla kernel: [   14.820971] wlan: 0.9.4
May  2 01:50:07 Watilla kernel: [   14.825998] ath_pci: 0.9.4
May  2 01:50:07 Watilla kernel: [   14.826057] ath_pci 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
May  2 01:50:07 Watilla kernel: [   14.874710] ath_pci 0000:02:00.0: PCI INT A disabled
```

My card is

```
02:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

```

---

### Post by Cybie257 on 2009-05-02
I hate to say this, but it happened recently to a friend.. (this is just my initial thought when I saw your post)

Be sure your WIFI switch is turned on. See you users manual if you don't know how to be sure it is on. 

It might sound like a lame thing, but it's happened. :)

-Cybie

---

### Post by macabro22 on 2009-05-02
> **Cybie257 said:**
> I hate to say this, but it happened recently to a friend.. (this is just my initial thought when I saw your post)

Be sure your WIFI switch is turned on. See you users manual if you don't know how to be sure it is on. 

It might sound like a lame thing, but it's happened. :)

-Cybie

Yeah, I know sometimes its something dumb. I did verify that though. Any other clues?

---

