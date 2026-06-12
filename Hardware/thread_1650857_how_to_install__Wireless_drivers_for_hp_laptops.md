---
title: "how to install  Wireless drivers for hp laptops  ??"
date: 2010-12-22
forum: Hardware
---

### Post by vinxtreme on 2010-12-22
Hi  all 


              I am using a hp pavilion dv6 laptop and have just installed Ubuntu 10.10 64 bit version .. 
I know there is a bug with hp mini's and there are a lot of threads explaining how to install b43 and STA drivers but nothing is working


can anybody plz tell whats path in this code ??? 

```

```# mkdir hybrid_wl
```

```# cd hybrid_wl
```

```# tar xzf <path>/hybrid-portsrc_x86-32_v5.60.246.6.tar.gz

the link to the code is ..
[HTML][/HTML][http://www.broadcom.com/docs/linux_sta/README.txt](http://www.broadcom.com/docs/linux_sta/README.txt)

mine is a fresh installation and not and upgrade ....plz help

TIA

---

### Post by coffeecat on 2010-12-22
If you have a Broadcom wireless card don't make life difficult for yourself by compiling the driver from source. Have a look at the "official" community documentation page here:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---

