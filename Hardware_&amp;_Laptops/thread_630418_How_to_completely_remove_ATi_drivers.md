---
title: "How to completely remove ATi drivers?"
date: 2007-12-03
forum: Hardware &amp; Laptops
---

### Post by Melhisedek on 2007-12-03
Helo there folks,
well in trying to get WoW to work I removed restricted drivers that came with Ubuntu 7.10, than installed 8.40.4 drivers (supposedly they would work best with WoW) but it was the same problem as before. So I wanted latest drivers back so I can have Compiz back. Now everything is soooo slow its not even funny.

So I want to remove everything and try to install restricted drivers from Synaptec manager again.

---

### Post by Yellow Pasque on 2007-12-03
If you just did a normal/express install of the 8.40.4:
```
cd /usr/share/ati
sudo sh ./fglrx-uninstall.sh
```

If you installed by building packages, you'll have to remove those packages.

For more info: [https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_cat711-inst.html](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_cat711-inst.html)

As for the ubuntu proprietary stuff:
Go to System -> Administration -> Restricted Driver Manager; uncheck the enabled box.

---

### Post by xfearxnxloathing on 2007-12-06
> **Temüjin said:**
> If you just did a normal/express install of the 8.40.4:
```
cd /usr/share/ati
sudo sh ./fglrx-uninstall.sh
```

If you installed by building packages, you'll have to remove those packages.

For more info: [https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_cat711-inst.html](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_cat711-inst.html)

As for the ubuntu proprietary stuff:
Go to System -> Administration -> Restricted Driver Manager; uncheck the enabled box.

i cannot even get to restricted drivers, **Your hardware does not need any restricted drivers**

---

### Post by Yellow Pasque on 2007-12-06
> **xfearxnxloathing said:**
> i cannot even get to restricted drivers, **Your hardware does not need any restricted drivers**

So, what kind of video card do you have? If you're not sure:
```
sudo update-pciids
lspci | grep "VGA"
```

---

