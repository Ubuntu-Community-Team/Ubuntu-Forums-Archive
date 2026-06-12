---
title: "PROLINK PixelView PlayTV Cinema BX1500 TV card"
date: 2013-08-07
forum: Hardware
---

### Post by iskeledz on 2013-08-07
Hi, I'm running Linux Mint 12 32-bit (the equivalent of Ubuntu 11.10) with the 3.2.49 kernel and I have the TV card from the title.
Manufacturer's website: [http://www.prolink.com.tw/style/frame/templates15/product_detail.asp?lang=2&customer_id=1470&name_id=36169&rid=17744&id=79936&content_set=color_5](http://www.prolink.com.tw/style/frame/templates15/product_detail.asp?lang=2&customer_id=1470&name_id=36169&rid=17744&id=79936&content_set=color_5)

I have properly installed the latest V4L drivers following this guide: [http://linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers](http://linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers)
However, it looks like the driver doesn't have support for this particular card as noted in the first warning in the above article. The proper kernel module (cx23885) loads, but it doesn't do anything. I've tried it with MythTV, Kaffeine and VLC and all of them report that there is no capture card.

This is the output of lspci -v:
```

04:00.0 Multimedia video controller: Conexant Systems, Inc. CX23885 PCI Video and Audio Decoder (rev 02)
    Subsystem: PROLINK Microsystems Corp Device 4980
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at fbe00000 (64-bit, non-prefetchable) [size=2M]
    Capabilities: [40] Express Endpoint, MSI 00
    Capabilities: [80] Power Management version 2
    Capabilities: [90] Vital Product Data
    Capabilities: [a0] MSI: Enable- Count=1/1 Maskable- 64bit+
    Kernel driver in use: cx23885
    Kernel modules: cx23885

```

The output of dmesg is here: [http://pastebin.com/yVK2NE3u](http://pastebin.com/yVK2NE3u)
Trying to modprobe the module with other card ids just spits out a bunch of errors in dmesg.

I wonder what (if anything) I can do to make the card work. If nothing else, I hope you could direct me somewhere where I could request support for the card to be added to the driver.

---

