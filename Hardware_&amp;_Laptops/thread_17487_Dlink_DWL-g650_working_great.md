---
title: "Dlink DWL-g650 working great"
date: 2005-02-28
forum: Hardware &amp; Laptops
---

### Post by jsaints on 2005-02-28
Hi all just wanted to post this info.

My Dlink DWL-g650 pcimcia network card was detected automatically by ubuntu. I could see my router via the "iwlist scan" command, but could not receive an IP via DHCP.  

I modified /etc/network/interfaces file and changed the line

wireless_key MY_KEY_GOES_HERE

to 

wireless_key1 MY_KEY_GOES_HERE

and now I can connect without problems.  I am not sure why this helps, just thought i would pass the info along.

---

### Post by jsgotangco on 2005-03-02
I'm using a DWL-G650+ (PCMCIA) - didn't work out of the box but worked with NDISWRAPPER along with my Realtek RTL8180 Mini-PCI.

```
wlan0: ndiswrapper ethernet device 00:0d:f0:10:5c:c3 using driver rtl8180.sys
ndiswrapper device wlan0 supports WPA with AES/CCMP and TKIP ciphers
ndiswrapper: driver rtl8180.sys (Realtek,10/07/2004,5.173.1007.2004) added
ACPI: PCI interrupt 0000:03:00.0[A] -> GSI 11 (level, low) -> IRQ 11
ndiswrapper: using irq 11
wlan1: ndiswrapper ethernet device 00:80:c8:2e:57:12 using driver gplus.sys
ndiswrapper device wlan1 supports  WPA with TKIP cipher
ndiswrapper: driver gplus.sys (D-Link,04/09/2004,6.0.0.18) added
```

Better than nothing hehehehe...

---

### Post by smtanner on 2005-03-02
You shouldn't need ndiswrapper to get the d-link G650 working.  It uses the atheros chipset (at least the one I have does) which is supported by the madwifi driver.  This driver is located in the linux-restricted package.  It is on the cd but is not installed by default for some reason.  Just install it and you should be ok.

---

### Post by blahrus on 2005-03-03
[QUOTE=smtanner]You shouldn't need ndiswrapper to get the d-link G650 working.  It uses the atheros chipset (at least the one I have does) which is supported by the madwifi driver.  This driver is located in the linux-restricted package.  It is on the cd but is not installed by default for some reason.  Just install it and you should be ok.[/QUOTE]
 yea, you should check linux-restricted-modules works like a charm, so nice not having to compile drivers, thats the ONLY thing that hasn't been supported by the kernel for my system in a long time, nice to see ubutnu add a package that includes it.

---

### Post by jsgotangco on 2005-03-03
Unfortunately, G650+ (note the + sign) uses TI, not Atheros so Ndiswrapper is the only way at the moment (as far as I know). What's important is that it works no matter how unnatural it looks. Next time, I'm checking what's fully compatible before buying :)

---

