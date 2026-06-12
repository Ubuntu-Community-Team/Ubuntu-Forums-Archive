---
title: "Lenovo T400 with WiFi Link 5300 :("
date: 2008-11-30
forum: Hardware
---

### Post by addicha on 2008-11-30
Quick Story:
I bought a Lenovo T400 Laptop with WiMAX 5350 card but since its not supported under linux yet I bought a regular Intel 5300 to use with Ubuntu. Unfortunately, Lenovo BIOS looks at the cards information and does not let the laptop boot up  unless its a Lenovo card. :( 

So, If anyone with a Lenovo laptop using WiFi Link 5300 give me the Lenovo Vendor ID, Product ID and Subsystem ID for this card I would really appreciate it... Seems I can use Lenovo numbers to reprogram my card and trick my BIOS.

You can see this with: lspci -v

Thanks,

---

### Post by addicha on 2008-12-01
Never mind. I found the list under: [http://pciids.sourceforge.net/](http://pciids.sourceforge.net/)

Hope it helps.

Regards

---

### Post by HankB on 2008-12-06
Did you get your 5300 working correctly? I have a T500 with the 5300 WiFi from Lenovo and it is recognized as a 5100:
```

03:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100
        Subsystem: Intel Corporation Device 1011
        Flags: bus master, fast devsel, latency 0, IRQ 2297
        Memory at f4300000 (64-bit, non-prefetchable) [size=8K]
        Capabilities: [c8] Power Management version 3
        Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
        Capabilities: [e0] Express Endpoint, MSI 00
        Capabilities: [100] Advanced Error Reporting <?>
        Capabilities: [140] Device Serial Number 82-e5-02-ff-ff-6a-21-00
        Kernel driver in use: iwlagn
        Kernel modules: iwlagn
```

I'm not putting this together with the information at the site you linked, but I'm still working on my first cup of coffee (literally. ;) )

thanks,
hank

---

### Post by bettlebrox on 2009-01-03
There are Debian instructions for getting the 5350 to work, this should probably work under Ubuntu too:
[http://wiki.debian.org/iwlagn](http://wiki.debian.org/iwlagn)

---

### Post by khalaf on 2009-09-07
To solve the 5300 wifi adapter problem, simply right click My Computer, Click properties, Click Device Manager.  Click Network Adapters.  Right click the Intel 5300 adapter. Select Unintstall.    
Restar your computer. WIFI will wake up again.
Good luck .
Khalaf

---

### Post by Private_Ops on 2009-09-07
> **khalaf said:**
> To solve the 5300 wifi adapter problem, simply right click My Computer, Click properties, Click Device Manager.  Click Network Adapters.  Right click the Intel 5300 adapter. Select Unintstall.    
Restar your computer. WIFI will wake up again.
Good luck .
Khalaf

:confused::confused::confused:

He's in Ubuntu dude.

---

