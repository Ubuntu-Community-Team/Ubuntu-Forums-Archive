---
title: "Problem with IrDA SIR interface, no driver."
date: 2008-01-04
forum: Hardware &amp; Laptops
---

### Post by endrre on 2008-01-04
I have a 2-in-1 bluetooth and IrDA usb dongle produced by SDM (Speed Dragon Multimedia). Productinformation: [http://www.speeddragon.com/Default/ProductInfo/Id/131]("http://www.speeddragon.com/Default/ProductInfo/Id/131")

Linux doesn't recognize the irda unit.

Here's the output from lsusb:
```

Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 1131:1001 Integrated System Solution Corp. KY-BT100 Bluetooth Adapter
Bus 001 Device 003: ID 1685:0200  
Bus 001 Device 002: ID 0451:2036 Texas Instruments, Inc. TUSB2036 Hub
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  

```

The 1685:0200 is the device. Queries from Google returned nothing or non-relevant information. It's been supported since windows98, where the driver is fairly small (30 kB), if that matters. It has a Tanic S110 chipset.

My question is: since it's a SIR unit (standard/slow infra red), will it go well together with general SIR drivers as well? My hardware hacking abilities are non-existant (but I do have some little programming experience), but do there exist some kind of method that I can follow or what?

---

