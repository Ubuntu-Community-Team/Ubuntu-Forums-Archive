---
title: "Canon MG7170 printer and scanner"
date: 2014-08-23
forum: Hardware
---

### Post by satimis on 2014-08-23
Hi all,

OS - Ubuntu 12.04 desktop 64bit.

I expect to buy a scanner with higher scanning resolution.  I found Cannon MG7170 in the market here.

MG7170 Specifications
[http://support-asia.canon-asia.com/contents/ASIA/EN/6200177100.html](http://support-asia.canon-asia.com/contents/ASIA/EN/6200177100.html)


However it is NOT listed here;
Manufacturer: Canon
[http://www.sane-project.org/sane-mfgs.html#Z-CANON](http://www.sane-project.org/sane-mfgs.html#Z-CANON)


I found the driver can be download on;
Canon Pixma MG7170 Free Download Driver
[http://ameliesite.wordpress.com/page/28/](http://ameliesite.wordpress.com/page/28/)

Is it for both printer and scanner?  Can this scanner work on Linux without problem?  Please shed me some light.

Thanks

Regards
satimis

---

### Post by pdc on 2014-08-23
Hi there satimis; welcome to the Ubuntu forums;

Canon supply linux drivers for the printer and scanner functions of this device;

Ubuntu uses debian packages; so the download site you cited only has the rpm package that I could see:

one gets the Canon debian printer driver from here [http://support-asia.canon-asia.com/contents/ASIA/EN/0100551202.html#r=s&r=s](http://support-asia.canon-asia.com/contents/ASIA/EN/0100551202.html#r=s&r=s) and it comes down as [COLOR="#008000"]cnijfilter-mg7100series-4.00-1-deb.tar.gz
[/COLOR]
and for the scanner, Canon supply a programme called **[COLOR="#0000FF"]ScanGearMP[/COLOR]**; you get it from here [http://support-asia.canon-asia.com/contents/ASIA/EN/0100552902.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100552902.html) and it comes down as [COLOR="#008000"]scangearmp-mg7100series-2.20-1-deb.tar.gz
[/COLOR]
_______________________________________________

I would believe it would work well with the programmes that Canon provide above: they do have access to the hardware to test the software that they supply!

If you buy the device, please post back and I can give you the details on how to get the printer and scanning functions working

_______________________________________________

I see that in SANE your device is mentioned; it is the 7100series; (you have the 7170 model of the 7100 series); if you buy it, you can help them

---

### Post by satimis on 2014-08-24
Hi,

Thanks for your advice.

I may change my selection because I didn't find Canon MG7170 support slide/negative scanning.  The color of some old photos are fading out.  I need to scan their negatives (I hope I still can find them on shelves).

My old Epson Scanner (Perfection 3490) has this feature.  I wonder whether it can work.  I would find some negavtives testing it.

Printing is NOT important to me. In 1~2 month I only print 1/2 document (sigle page).  My old HP Deskjet 5740 printer still works.  Even though I need to push the paper to the printer.

I found Canon Scan 9000F Mark II Professional CCD Scanner here.  I suppose it is the same as "CanoScan 9000F Mark II".  The scanner is supported by SANE.


SANE: Supported Devices
[http://www.sane-project.org/sane-mfgs.html#Z-CANON](http://www.sane-project.org/sane-mfgs.html#Z-CANON)
```

CanoScan 9000F Mark II 	
USB 	0x04a9/0x190d 	Complete 	
Full flatbed support up to 4800DPI (Note: flatbed does not have 9600DPI capability). 
Full TPU support (negatives, slides and infrared) up to 9600DPI.

```
Specfication
[http://www.bhphotovideo.com/c/product/905050-REG/Canon_6218b002aa_CS_9000F_Mark_II_Image.html](http://www.bhphotovideo.com/c/product/905050-REG/Canon_6218b002aa_CS_9000F_Mark_II_Image.html)
-> Specification

Nice features.  Actually what I need is a high quality scanner which can scan slides/negatives as well

Comment and suggestion would be appreciated.  Thanks

Regards
satimis

---

