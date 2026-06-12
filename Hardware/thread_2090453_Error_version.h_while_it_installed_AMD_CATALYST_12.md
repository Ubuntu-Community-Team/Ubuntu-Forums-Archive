---
title: "Error version.h while it installed AMD CATALYST 12.11 beta8 driver"
date: 2012-12-02
forum: Hardware
---

### Post by Broobie on 2012-12-02
I use Quantal (12.10) and when I was installing AMD Catlyst 12.11 beta8 driver I got this error (fglrx-install.log):

```
fglrx installation requires that the system have kernel headers.  /lib/modules/3.5.0-19-generic/build/include/linux/version.h cannot be found on this system.

```


And I go where path says and "/build/include/linux/version.h" doesn't exist, any folder or file of them. :confused:

---

### Post by Yellow Pasque on 2012-12-02
You need the linux-headers-generic package. Follow the instructions here: [http://wiki.cchtml.com/index.php/Ubuntu_Quantal_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29_BETA.2FEXPERIMENTAL](http://wiki.cchtml.com/index.php/Ubuntu_Quantal_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29_BETA.2FEXPERIMENTAL)

---

### Post by Broobie on 2012-12-02
Great link! All works fine now!

---

