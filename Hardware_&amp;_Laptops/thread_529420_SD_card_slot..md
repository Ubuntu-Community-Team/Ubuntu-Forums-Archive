---
title: "SD card slot."
date: 2007-08-19
forum: Hardware &amp; Laptops
---

### Post by Auax on 2007-08-19
My Acer Aspire 5100 has a built in SD Card slot, and it does nothing when I put the card in. Can someone direct me to a driver package or whatever I need to make it work. It's annoying to have to boot into Vista just to get my photos.

---

### Post by Auax on 2007-08-26
Help?

I also eh... kinda destroyed Vista, so now I have to go to walmart to get my pictures. :|

---

### Post by hessiess on 2007-08-26
dusnt the camara have a usb conection?

---

### Post by Auax on 2007-08-26
I lost the cord ages ago.

---

### Post by hessiess on 2007-08-26
carnt you find a new cable, thay are normaly fairly standerdised

you may haft to get a usb reader

if you run

lspci

can you see anything like sd card controler?

i get these two
```

08:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
08:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
```

---

### Post by Auax on 2007-08-26
```

06:04.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
06:04.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
06:04.2 Generic system peripheral [0805]: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01)
06:04.3 FLASH memory: ENE Technology Inc FLASH memory: ENE Technology Inc: (rev 01)
06:04.4 FLASH memory: ENE Technology Inc Unknown device 0551 (rev 01)

```

---

### Post by hessiess on 2007-08-26
so its found the card reader controler, but for some resen its not working.
i cannot help any further, my knolage is fairly limated. 

you could try sertching for 

ENE Technology Inc ENE PCI Secure Digital Card Reader Controller+ linux driver
or 
Acer Aspire 5100+ linux problems

---

