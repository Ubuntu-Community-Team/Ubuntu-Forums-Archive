---
title: "Fujitsu-Siemens Amilo L7310W Laptop"
date: 2006-09-09
forum: Hardware &amp; Laptops
---

### Post by doerian on 2006-09-09
[QUOTE=wickwire;1094544]_Fujitsu-Siemens Amilo L7310W Laptop_

With Dapper 6.06:

```
0000:00:00.0 Host bridge: VIA Technologies, Inc. CN400/PM880 Host
skip...

[INDENT]My new laptop, the only one I could find without WIN preinstalled, looks very much like this one, so I am happy with this information.[/INDENT]



0000:01:00.0 VGA compatible controller: VIA Technologies, Inc. S3 Unichrome Pro VGA Adapter (rev 02)
```

Issues:

**irqpoll** on the grub kernel line allows for:

USB 2.0 on all three usb ports;
no more sluggish USB mouse movement;
CD/DVD recorder ( PHILIPS DVD+/-RW SDVD8431 Firmware Revision:  LJ41 ) won't "crash" while burning a session - along with DMA enabled, no more issues burning files;
WIFI working with all the rest - wasn't a sure thing without **irqpoll**.

via graphics driver works, 
[INDENT]My question: Is this the proprietary driver? Is the XOrg driver not yet ready for Unichrome PRO?[/INDENT]
 


[INDENT]thanks in advance
hansr

[/INDENT]

---

### Post by mnhercules84 on 2007-01-27
Same thing here. Any solutions? I don't have 1280x800 screen resolution.
On knopix everything wokrs just fine.

---

### Post by kulik on 2007-01-27
just write 1280x800 in your /etc/X11/xorg.conf and it will go.
ive got l7320gw, and i cant switch my fun
how about your fan? is it switching like in winxp?

---

### Post by mnhercules84 on 2007-01-30
Tnx very much I managed to do it. It is working fine. 
Just my bot up screen is still moved to the left or right whatevr :(
Any solutions?

Fan is working just like in Win XP

---

### Post by lill-eric on 2008-05-21
> **kulik said:**
> just write 1280x800 in your /etc/X11/xorg.conf and it will go.
ive got l7320gw, and i cant switch my fun
how about your fan? is it switching like in winxp?


I'm running hardy on a l7320gw. The only problem right now is with graphics. All I realy want is better resolusion than 800x600. 
Perhaps a nube question, but: Where am I supposed to write 1280x800?
Can't seem to find any apropriate place for it in my xorg.xonf.

-E

---

