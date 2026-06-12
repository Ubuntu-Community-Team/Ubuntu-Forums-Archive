---
title: "Scanner on Ubuntu server"
date: 2012-11-03
forum: Hardware
---

### Post by Jbwhite on 2012-11-03
Hello,

I have recently built a home server with ubuntu server on it.
So far I have configured it as a printer server using samba and CUPS. I also want to have it as a scanner server. I have a HP Photosmart C4680 All-in-One and i can't seem to get sane to recognise it. When I type sane-find-scanner it detects it as a hp photosmar C4600 series, but when i type scanimage -L it says no scanners were identified.

Please Help

Ubuntu server 12.04.1

---

### Post by SeijiSensei on 2012-11-03
I don't see that model in the list of HP scanners that SANE supports:

[http://www.sane-project.org/sane-mfgs.html#Z-HEWLETT-PACKARD](http://www.sane-project.org/sane-mfgs.html#Z-HEWLETT-PACKARD)

You're not alone.  I have a nice Scanjet that I got for free, but it won't work with SANE either.

---

### Post by daxelinxe on 2012-12-23
> **Jbwhite said:**
> Hello,

I have recently built a home server with ubuntu server on it.
So far I have configured it as a printer server using samba and CUPS. I also want to have it as a scanner server. I have a HP Photosmart C4680 All-in-One and i can't seem to get sane to recognise it. When I type sane-find-scanner it detects it as a hp photosmar C4600 series, but when i type scanimage -L it says no scanners were identified.

Please Help

Ubuntu server 12.04.1
I have a HP 4500 Photosmart all in one.
It works perfectly well with Ubuntu 12-04 LTS 32-bit- (Print and scan).
But I am using now the 12-04 LTS server 64bit : printing is O.K. but no scan at all.
I have tried everything since and guess the problem is hopeless.....!!

---

