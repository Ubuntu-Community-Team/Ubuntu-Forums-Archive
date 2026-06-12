---
title: "HP Officejet 6500 not auto detected by xsane - scanimage with device URL works"
date: 2018-08-12
forum: Hardware
---

### Post by phil1982 on 2018-08-12
Dear all,

I'm trying to scan something with xsane but i'm unable to do so:
Problem is that i'm unable to detect my wifi network scanner with scanimage -L or when invoking xsane or simple scan. 
As i'm usually scanning from a shell script for which i recorderd the scan URL i'm still able to scan if i tell scanimage the device URL. For xsane however i can't do that. sane-find-scanner doesn't find scanners either. This seems to be since i upgraded from 16.04 to 18.04

So to summarize

[LIST]
[*]My goal is to use xsane. 
[*]This fails as xsane is not detcting any devices (as does scanimage -L) after launched 
[*]invoking scaneimage with device on the cli works (e.g. scanimage -d hpaio:/net/Officejet_6500_E710n-z?zc=HPE87D94 > test1.jpg works fine) 
[*]my scanner is an HP Officejet 6500 E710n-z all in one mfd 
[*]in 16.04 things were fine. In 18.04 where i'm now it's not 
[/LIST]

Things i already tried were:
[LIST]
[*]invoke xsane with sudo 
[*]purge / reinstall libsane and sane-utils 
[*]sane-find-scanner doesn't find the scanner either. Hence the tutorial [https://help.ubuntu.com/community/SANE%20-%20Installing%20a%20scanner%20that%20isn%27t%20auto-detected](https://help.ubuntu.com/community/SANE%20-%20Installing%20a%20scanner%20that%20isn%27t%20auto-detected) doesn'T work either 
[/LIST]

Any Ideas?

Best Regards
Philipp

---

### Post by Autodave on 2018-08-13
Upgrading can often cause such problems and is why I don't do it anymore: I do clean installs.  Have you installed *hplip* yet?  You may have to do that to get the scanner portion recognized.

Just a heads up for you and others: when I wiped 16.04 and did a clean install of 18.04, my *wireless *HP laser scanner/printer was turned on. The installer found it and installed EVERYTHING without me having to do a thing.

---

