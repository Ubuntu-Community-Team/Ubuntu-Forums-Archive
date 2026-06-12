---
title: "Samsung SCX-4016 driver needed"
date: 2005-12-20
forum: Hardware &amp; Laptops
---

### Post by pvlbill on 2005-12-20
Samsung.com has linux driver for the MFP SCX-4016 on their web site, however, I can not get it to load properly. Any help would be appreciated. :confused: 

I am using Breezy on a Dell Dimension L733r computer.

---

### Post by xombie on 2005-12-21
I bought my dad an SCX-4100. I had the false belief that Samsung's drivers were still open source like they where years ago. When I went to install the mfp drivers I was very disappointed in the quality of their code and installer. The Moscow design center should be ashamed. While I can't help you specifically I will show what I did to install the 4100. The 4100 and 4016  both share the same driver pack.

I did not want to use their gui because cups and xsane are just fine. So I extracted the files I needed and wrote my own install script. Their code has some wierd file dependencies though so I had to install stuff that really is not needed like libqt.
> 
#!/bin/sh
##printer files
cp -a -f rastertosamsungspl /usr/lib/cups/filter/
chmod 755 /usr/lib/cups/filter/rastertosamsungspl
cp -a -f scx4100.ppd /usr/share/cups/model/
chmod 755 /usr/share/cups/filter/scx4100.ppd
##lib files
cp -a -f libmfp.so.1.0.1 /usr/lib/
chmod 644 /usr/lib/libmfp.so.1.0.1
cp -a -f libmfpdetect.so.1.0.1 /usr/lib/
chmod 644 /usr/lib/libmfpdetect.so.1.0.1
cp -a -f libqt-mt.so.3.0.4 /usr/lib/libqt-mt.samsung-mfp.so.3.0.4
chmod 644 /usr/lib/libqt-mt.samsung-mfp.so.3.0.4
##scanner files
cp -a -f libsane-samsung_scx4100.so.1.0.1 /usr/lib/sane/
chmod 644 /usr/lib/sane/libsane-samsung_scx4100.so.1.0.1
echo "samsung_scx4100" | cat /etc/sane.d/dll.conf - | tr -s ["\n"] > /etc/sane.d/dll.conf
chmod 644 /etc/sane.d/dll.conf
##make links
/sbin/ldconfig -n /usr/lib/sane /usr/lib
 
The above script should give you an idea were things need to go with proper permissions. You will need to extract the files you need from their cdroot folder into your own install folder and name your script something like scx4016.install and put that in the folder as well. Some of the files you will need are buried in sub archives ending in .ss or .sx. The driver pack has 3 rastertosamsung drivers,  the 4100 uses the spl version.  Yours my use a different one.

Good luck

---

### Post by pvlbill on 2006-01-03
[QUOTE=pvlbill]Samsung.com has linux driver for the MFP SCX-4016 on their web site, however, I can not get it to load properly. Any help would be appreciated. :confused: 

I am using Breezy on a Dell Dimension L733r computer.[/QUOTE]

Found answer to installation problem on a posting by NEUROSION. Used his how-to on another printer and it worked with slight tweaking. Appreciate the help available on these forums!

---

