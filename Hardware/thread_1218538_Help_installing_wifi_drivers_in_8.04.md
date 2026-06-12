---
title: "Help installing wifi drivers in 8.04"
date: 2009-07-20
forum: Hardware
---

### Post by mavis311 on 2009-07-20
I just installed 8.04 on my laptop due to a video driver incompatibility issue under 9.04.  

Current problem is that my wireless hardware (Realtek RTL8187B) is apparently not supported.  There are no wireless networks listed.  I found a driver for my wifi at [http://rtl-wifi.sourceforge.net/wiki/Installing](http://rtl-wifi.sourceforge.net/wiki/Installing) but I can't complete the installation.  I get to the part where I need to "insmod" the modules I built, but I get an error: 

```
mavis@rigel:~/DRIVERS/rtl-wifi$ sudo insmod ieee80211/ieee80211_crypt-rtl.ko
insmod: error inserting 'ieee80211/ieee80211_crypt-rtl.ko': -1 File exists
```

What can I do to be able to proceed?

Also, I need to change the key used to acces the router after I get the drivers installed (i.e.-key 1, key 2, key 3, key 4 -- I can't find a place to set that option in 8.04)

---

