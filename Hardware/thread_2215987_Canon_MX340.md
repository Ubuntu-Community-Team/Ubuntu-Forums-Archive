---
title: "Canon MX340"
date: 2014-04-09
forum: Hardware
---

### Post by nick96 on 2014-04-09
I'm helping a client to get Ubuntu to work with his printer. Regular printing and scanner use seem to work well on the stock drivers for Ubuntu however he wants to be able to use the multi-feed to scan multiple pages at once. I've looked at gscan2pdf and vuescan  however gscan2pdf throws a error code whenever I try it and vuescan will throw an error if I try to scan multiple pages(Quits after the first page). Any quick fixes to those errors? My client is also wondering if we could somehow use the original software so he can scan multiple pages and make them into PDF's. I tried to do it through wine despite my disbelief and it throws up an error about a problem with printer spools when trying to install the software.

---

### Post by pdc on 2014-04-09
so this is a 4yr old device; one could suggest evaluating the driver Canon supplied in Feb 2010; it is called scangearmp and is for 32bit system; as was current then; [http://support-asia.canon-asia.com/contents/ASIA/EN/0100272801.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100272801.html)

it comes down as scangearmp-mx340series-1.50-1-i386-deb.tar.gz

commands to install from a terminal would be:

cd Downloads
tar zxvf scangearmp-mx340series-1.50-1-i386-deb.tar.gz
cd scangearmp-mx340series-1.50-1-i386-deb
./install.sh

(I suspect all that you mention were only intended for single page use)

---

### Post by nick96 on 2014-04-10
No my client wants to use the multi-feed scanner not the flatbed. Oh yeah, I forget to mention. The computer is using Ubuntu 12.04 LTS 32-bit.

---

### Post by nick96 on 2014-04-11
Bump.

---

### Post by aikishugyo on 2014-04-14
Multi-feed means ADF (automatic document feeder) I think.
You could try SANE, there has been progress debugging the use of this on various Canon all-in-ones in recent weeks,
so perusing the mailing list, and taking part there would be useful---for all I know, your device is already fully supported for ADF.

---

