---
title: "Wireless driver disconnecting every few minutes then connects again"
date: 2011-10-30
forum: Hardware
---

### Post by TheNavigator on 2011-10-30
Driver:

```
Broadcom 802.11 Linux STA wireless driver
```I installed Ubuntu server by mistake first, then I removed it and install Ubuntu desktop. After few days grub had a massive problem, I reinstalled it and it didn't work, then I reinstalled it again and it worked. After a week or something, that problem happens. The network frequently disconnects and connects again. It's really annoying. Can someone help? :)

EDIT:

I'm using Laptop Dell Latitude E6500

---

### Post by TheNavigator on 2011-10-31
Anyone?

---

### Post by TheNavigator on 2011-11-01
So?...

---

### Post by TheNavigator on 2011-11-02
Will someone help? :(

---

### Post by TheNavigator on 2011-11-09
Heeeeeeeelp?

---

### Post by TheNavigator on 2011-11-12
Please help...

---

### Post by TheNavigator on 2011-11-14
I really need help.. :(

---

### Post by TheNavigator on 2011-11-20
Anyone?

---

### Post by diasf on 2011-11-20
Need more info. Any relevant output from dmesg? Are you sure the channel isn't crowded?

---

### Post by TheNavigator on 2011-11-22
What's dsmeg?

And yea I'm pretty sure, and the most reason why I'm sure is because it works perfectly on Vista

---

### Post by emilywind on 2011-11-22
dmesg tells about system related events. After it happens, give us the output of:

```
dmesg | tail
```

Also, are you using the closed or open source broadcom driver? If using the closed source, please remove it and try using the open source driver as it is rumoured to have less issues (which should be called in by default after the closed source one is removed). If you are using the closed source one you would have installed it via the additional drivers dialogue. Cheers.

---

