---
title: "Ubuntu 12.04 LTS , Canon i-SENSYS LBP3250"
date: 2013-03-18
forum: Hardware
---

### Post by sandeepnaik on 2013-03-18
[SIZE=3][FONT=book antiqua]Hello, I have installed Ubuntu 12.04 LTS on my PC.

But I could not run my Canon i-SENSYS LBP3250 laser printer on it.

I have disabled SElinux and also installed CAPT Printer Driver for Linux V2.20 but still my printer is not printing.

Whenever I submit a print job, in printer properties it shows 'processing-sending data to printer' but nothing happens!

Can anyone help me?[/FONT][/SIZE]

---

### Post by dino99 on 2013-03-18
searching "canon" inside synaptic, should tell you to install: printer-driver-cjet

---

### Post by pdc on 2013-03-18
a crucial element in installing the CAPT driver is to disclose if you have a 32bit or 64bit install

I think this tutorial by Sivella; (hopefully translated from french to english); is the best source;

[http://translate.google.co.nz/translate?sl=fr&tl=en&js=n&prev=_t&hl=en&ie=UTF-8&eotf=1&u=http%3A%2F%2Fdoc.ubuntu-fr.org%2Ftutoriel%2Finstaller_pilote_canon_lbp](http://translate.google.co.nz/translate?sl=fr&tl=en&js=n&prev=_t&hl=en&ie=UTF-8&eotf=1&u=http%3A%2F%2Fdoc.ubuntu-fr.org%2Ftutoriel%2Finstaller_pilote_canon_lbp)

he starts by describing a 64bit install; as there are tweaks needed if one has 64bit; then the waters become smoother;

let us know more details of what you did; 

if you go here (Canon Asia): Canon is based in Asia ...

[http://support-asia.canon-asia.com/contents/ASIA/EN/0100459601.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100459601.html)

you will see that the CAPT driver is up to [COLOR="#0000FF"]2.5[/COLOR] and comes down as [COLOR="#008000"]Linux_CAPT_PrinterDriver_V250_uk_EN.tar.gz[/COLOR]

If you have only just installed 12.04 and see it as an LTS I can only suggest you install 32bit if you have not

best wishes

---

