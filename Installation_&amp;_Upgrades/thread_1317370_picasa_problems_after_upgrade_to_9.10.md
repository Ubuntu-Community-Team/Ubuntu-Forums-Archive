---
title: "picasa problems after upgrade to 9.10"
date: 2009-11-06
forum: Installation &amp; Upgrades
---

### Post by kellerf on 2009-11-06
After upgrade to 9.10 I cannot run picasa as user. It comes with the message:
kveta@hukot:~$ picasa 
/usr/bin/picasa: &#345;ádek 139:  7343 Segmentation fault "$PIC_BINDIR"/wrapper check_dir.exe.so
/usr/bin/picasa: &#345;ádek 175:  7446 Segmentation fault "$PIC_BINDIR/wrapper" regedit /E $registry_export HKEY_USERS\\S-1-5-4\\Software\\Google\\Picasa\\Picasa2\\Preferences\\

I tried to reinstall, it didn't help.
I can run picasa as root, though.

Thanks for any help.
F.

---

### Post by spiperman on 2009-11-07
I had a similar problem. I followed the instructions found at Google [ [http://picasa.google.com/linux/download.html#picasa30](http://picasa.google.com/linux/download.html#picasa30) ].  First I removed (NOT a complete removal) v2.7, then installed v3.  When run for the first time v3 found my previous configuration data and imported it. Everything then worked fine.  Hope this helps.

---

