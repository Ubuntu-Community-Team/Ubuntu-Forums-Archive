---
title: "VAIO IDE CD/DVD Not corectly Detected"
date: 2006-08-15
forum: Hardware &amp; Laptops
---

### Post by aka47 on 2006-08-15
](*,) 

I guess this could be a touch perenial but i have a problem (No kidding you say) with ide detection under Dapper 6.06 on a Sony Vaio VGN-FS295XP.

It originaly appeared to detect the CD/DVD OK and installed fine but following updates etc it seems to have become broken.

The Laptops has an IDE hard drive (factory set) as master on IDE0 and a CD/DVD drive (factory set) as slave IDE0.

dmesg reports :-

[17179571.548000] Boot video device is 0000:01:00.0
[17179572.056000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179576.068000]     ide0: BM-DMA at 0x1880-0x1887, BIOS settings: hda:DMA, hdb:DMA
[17179576.068000] Probing IDE interface ide0...
[17179599.136000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179603.044000] Probing IDE interface ide1...

I am running the linux686 kernel 2.6.15.24

Can anyone offer advice/sugestions as to what paremeters/tweaks I might need to use to get my CD/DVD drive recognised.

---

### Post by aka47 on 2006-08-15
Oh I forgot to add i am running the 2.6.15.26-686 kernel.:KS

---

