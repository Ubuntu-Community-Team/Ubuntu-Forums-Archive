---
title: "ATI X300 Driver"
date: 2006-12-05
forum: Hardware &amp; Laptops
---

### Post by Nirva on 2006-12-05
Hay, I tried installing the ATI X300 Driver so I followed this manual : 

[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)

I tried method 2 cause method 1 did not help for me.
But when I do this :

bash ati-driver-installer-8.29.6.run --buildpkg Ubuntu/edgy

Creating directory fglrx-install
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.29.6.............................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
-e ==================================================
-e  ATI Technologies Linux Driver Installer/Packager 
-e ==================================================
./ati-installer.sh: 176: Syntax error: Bad substitution
Removing temporary directory: fglrx-install
filip@Filip:~/Desktop$ 

Does anyone knows, how I can fix this?

---

### Post by pay on 2006-12-05
Maybe the installer got corrupted while it downloaded.

---

### Post by Nirva on 2006-12-06
I don't think so, cause I tried downloading it a second time, and I had the same error.

---

