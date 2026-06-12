---
title: "Scanner Epson PX720WD not detected"
date: 2010-11-18
forum: Hardware
---

### Post by danube on 2010-11-18
Hello folks;

I've recently bought an Epson multifunctional device, which also comes with a flat bed scanner. Epson claims the device to be supported (by third party drivers), that's why I've chosen this specifically.

I've tried a lot to get it running on my Ubuntu 10.10, both over USB and ethernet without success. Sane should get connected with iscan, but I can see no straight way or guideline how to get things started.

Can anyone help me please?
Thank you! Thomas

---

### Post by IcarusR on 2010-11-18
If you haven't already done so you need to download & install printer driver & iscan from avasys

[http://www.avasys.jp/lx-bin2/linux_e/spc/DL2.do]("http://www.avasys.jp/lx-bin2/linux_e/spc/DL2.do")

---

### Post by danube on 2010-11-18
> **IcarusR said:**
> If you haven't already done so you need to download & install printer driver & iscan from avasys

Thank you for replying. I've installed iscan drivers from avasys using the provided deb packages. Sane still won't find a connection to the device. :confused:

---

### Post by kliffs on 2010-11-18
If by multifunctional you mean printer you could start there otherwise check and see if there are linux drivers from epson.

---

### Post by IcarusR on 2010-11-19
Did you install core & data scanner .deb packages from avasys ? 
I believe iscan is a scanning app in it's own right, does this work ? Start from terminal
```
iscan
```

If it does not work what is the error ?

Does printing work ?
How is the machine connected ?

If it is networked you may have to set it up as per the userg_rev_e.pdf document on the avasys site.

---

### Post by peab on 2011-02-06
Having such a scanner connected on my LAN, I just had to delete the # before localhost in /etc/sane.d/net.conf to be able to use it with xsane.

BTW, reading userg_revL_e.pdf helped me to find it :)

---

