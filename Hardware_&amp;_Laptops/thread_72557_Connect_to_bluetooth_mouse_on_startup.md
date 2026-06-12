---
title: "Connect to bluetooth mouse on startup"
date: 2005-10-06
forum: Hardware &amp; Laptops
---

### Post by nickj6282 on 2005-10-06
I have a Dell Inspiron 600m with built in Truemobile Bluetooth. I bought a new bluetooth mouse today made just for notebooks. It works great, but everytime I turn on the PC I have to issue this command to get the mouse working:

```
sudo hidd -connect xx:xx:xx:xx:xx:xx
```

I tried adding the following line to my /etc/default/bluez-utils file, but I still have  to issue the above command in order to get the mouse working

```
HIDD_OPTIONS="-i xx:xx:xx:xx:xx:xx --server"
```

Any suggestions anyone?

Thanks
-Nick

---

