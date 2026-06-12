---
title: "Laptop Wireless not working"
date: 2004-10-18
forum: Hardware &amp; Laptops
---

### Post by UnknownQ on 2004-10-18
For some reason my wireless card is not being started like it should. dmesg shows the following errors:
ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 0.11
ipw2200: Copyright(c) 2003-2004 Intel Corporation
ACPI: PCI interrupt 0000:00:0b.0[A] -&gt; GSI 19 (level, low) -&gt; IRQ 19
ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
ipw2200: dmaWaitSync Failed
ipw2200: Unable to load boot firmware
ipw2200: Unable to load firmware: 0xFFFFFFFF
ipw2200: failed to register network device
ipw2200: probe of 0000:00:0b.0 failed with error -5

Great distro, by the way.

---

### Post by knappen on 2004-10-18
I would also like to know how you setup the IPW2200 card.

---

### Post by retrakker on 2004-10-19
[quote=UnknownQ]
ipw2200: Unable to load boot firmware
ipw2200: Unable to load firmware: 0xFFFFFFFF
ipw2200: failed to register network device
ipw2200: probe of 0000:00:0b.0 failed with error -5
[/quote]

It almost tells you what is missing ;). Be sure that the module can find the firmware*.  


* [http://ipw2200.sourceforge.net/firmware.php](http://ipw2200.sourceforge.net/firmware.php)

---

### Post by UnknownQ on 2004-10-19
[quote=retrakker]
It almost tells you what is missing ;). Be sure that the module can find the firmware*.[/quote]
I tried that: 
```

sam@greyviper&#58;~ $ ls /usr/lib/hotplug/firmware/
ipw2200_boot.fw  ipw2200_bss.fw  ipw2200_ibss.fw  ipw2200_ucode.fw
sam@greyviper&#58;~ $ ls /etc/firmware/
ipw2200_boot.fw  ipw2200_bss.fw  ipw2200_ibss.fw  ipw2200_ucode.fw

```
Still not working.

---

### Post by retrakker on 2004-10-19
```

sam@greyviper&#58;~ $ ls /usr/lib/hotplug/firmware/
ipw2200_boot.fw  ipw2200_bss.fw  ipw2200_ibss.fw  ipw2200_ucode.fw
sam@greyviper&#58;~ $ ls /etc/firmware/
ipw2200_boot.fw  ipw2200_bss.fw  ipw2200_ibss.fw  ipw2200_ucode.fw

```
Still not working.

what kind of kernel you are using? the original ubuntu kernel package comes with all modules installed in the right place. 

```

retrakker@blade ~ $ ls /usr/lib/hotplug/firmware/ipw*
/usr/lib/hotplug/firmware/ipw2100-1.2.fw-2.6.8.1-2-386
/usr/lib/hotplug/firmware/ipw2100-1.2-i.fw-2.6.8.1-2-386
/usr/lib/hotplug/firmware/ipw2100-1.2-p.fw-2.6.8.1-2-386
/usr/lib/hotplug/firmware/ipw2200_boot.fw-2.6.8.1-2-386
/usr/lib/hotplug/firmware/ipw2200_bss.fw-2.6.8.1-2-386
/usr/lib/hotplug/firmware/ipw2200_ibss.fw-2.6.8.1-2-386
/usr/lib/hotplug/firmware/ipw2200_ucode.fw-2.6.8.1-2-386

```

---

### Post by UnknownQ on 2004-10-19
[quote=retrakker]what kind of kernel you are using? the original ubuntu kernel package comes with all modules installed in the right place.
[/quote]
The default base install.

---

### Post by knappen on 2004-10-19
My firmware loads just fine but I cannot activate the connection.

I have set up the essid and WEP but still no success.

---

### Post by knappen on 2004-10-19
After the firmware is loaded should not the drivers be loaded as well? Sorry if it is a stupid question...

---

### Post by UnknownQ on 2004-10-22
*bump*
Problem still not solved.

---

### Post by knappen on 2004-10-22
Mine worked fine after 

modprobe ipw2200
modprobe firmware_class

---

### Post by HydroSan on 2005-10-21
[http://openthought.org/blosxom.cgi/2005/09/07#firmware_and_udev](http://openthought.org/blosxom.cgi/2005/09/07#firmware_and_udev)

Worked for me like a charm on both Ubuntu and Gentoo.

EDIT: Whoops - misread the date. Thought it read 2005.

---

