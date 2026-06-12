---
title: "Does a HP Photosmart C4795 work in Linux?"
date: 2010-07-03
forum: Hardware
---

### Post by geovino on 2010-07-03
I've recently installed Lubuntu 10.04 on a friends 6 yr old Compaq desktop and it works great. but my friend bought an Epson stylus mx110, the printer works but the scanner doesn't. No matter what I did it still wouldn't work. I brought my laptop with Ubuntu on it over and the printer did the same thing. Now I think that the Epson's scanner part is defective. would like to exchange for an HP all-in-one but the HP4480 is a bad one:
[http://www.openprinting.org/printers](http://www.openprinting.org/printers).

what other HP printer would work? I saw a Photosmart C4795 on sale but it's not listed, I hope the scanner works. Have anyone used this printer? I'd like to exchange it in two days but I don't know what to get.  

Will the Photosmart C4795 print and scan in Linux? Any other suggestions?

---

### Post by ajgreeny on 2010-07-03
Sure will, with full support from hplip.  The hplip version in Lucid is fine for this all-in-one.
[http://hplipopensource.com/hplip-web/models/photosmart/photosmart_c4700_series.html](http://hplipopensource.com/hplip-web/models/photosmart/photosmart_c4700_series.html)
Just add **hplip-gui** (you should already have hplip by default) and then open HPLIP Toolbox from the **System -Preferences** menu.  It's brilliant; better, I think, than in windows where there is always so much rubbish added software to install as well that you may never use.

---

### Post by geovino on 2010-07-03
> **ajgreeny said:**
> Sure will, with full support from hplip.  The hplip version in Lucid is fine for this all-in-one.
[http://hplipopensource.com/hplip-web/models/photosmart/photosmart_c4700_series.html](http://hplipopensource.com/hplip-web/models/photosmart/photosmart_c4700_series.html)
Just add **hplip-gui** (you should already have hplip by default) and then open HPLIP Toolbox from the **System -Preferences** menu.  It's brilliant; better, I think, than in windows where there is always so much rubbish added software to install as well that you may never use.

Thank you. I picked one up today. Will set up tomorrow. :)

---

### Post by geovino on 2010-07-04
The HP C4795 installed and runs perfectly.  

Thanks again.  :)

---

