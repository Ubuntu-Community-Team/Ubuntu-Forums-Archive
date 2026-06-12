---
title: "Card reader on TravelMate 4650 not working"
date: 2008-11-07
forum: Hardware
---

### Post by SilverAdder on 2008-11-07
I just installed Intrepid on an Acer TravelMate 4650, and the only thing that doesn't seem to work is the card reader. When I plug in an SD card nothing happens. It should auto-mount right? Any idea what is wrong, or what I might be doing wrong?

lshw: 
```
*-pcmcia
                description: CardBus bridge
                product: CB-712/4 Cardbus Controller
                vendor: ENE Technology Inc
                physical id: 4
                bus info: pci@0000:05:04.0
                version: 10
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192 module=yenta_socket
```

lspci: 
```
05:04.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
05:04.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
05:04.2 SD Host controller: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01)
05:04.3 FLASH memory: ENE Technology Inc FLASH memory: ENE Technology Inc: (rev 01)
05:04.4 FLASH memory: ENE Technology Inc SD/MMC Card Reader Controller (rev 01)
```

---

### Post by SilverAdder on 2008-11-07
Hopeful bump

---

