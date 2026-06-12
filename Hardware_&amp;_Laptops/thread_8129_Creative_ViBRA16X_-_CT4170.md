---
title: "Creative ViBRA16X - CT4170"
date: 2004-12-14
forum: Hardware &amp; Laptops
---

### Post by tmyster on 2004-12-14
Hello to All,

I am trying to figure out why my sound card will not initialize automatically. I have an ISA card that is PnP. I can see that its recognized during the startup process along with seeing it in the appropriate logs. 

_DMESG_: shows
isapnp: Scanning for PnP cards...
pnp: SB audio device quirk - increasing port range
isapnp: Card "Creative ViBRA16X PnP"
isapnp: 1 Plug & Play card detected total

_Kernel Log_: shows
sb: PnP: Detected at io=0x220 irq=5 dma=1 dma16=3
SB 4.16 detected OK (220)
SB16: Bad or missing 16 Bit DMA Channel.

When I enter a "lsmod" there is not a reference to sound or sb modules. But once I enter the "sudo msprobe sb" then enter "lsmod" again. The sound reference is there and the card works.

Can anyone tell me how to remedy this. Also ALSA displays a message at boot-up but it goes by too quickly for me to write down.

---

