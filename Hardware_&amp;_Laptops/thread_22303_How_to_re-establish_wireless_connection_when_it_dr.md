---
title: "How to re-establish wireless connection when it drops?"
date: 2005-03-26
forum: Hardware &amp; Laptops
---

### Post by akirafist on 2005-03-26
A few times per day, my wireless connection on eth1 will just drop for no reason.  How do I re-establish wireless connection after it drops?

I tried going into config and re-activating eth1, but it just hangs forever at the progress bar.  Typing **ifconfig eth1 up** doesn't do anything either, and it returns no error messages.

Rebooting works, but that's a huge pain when I'm in the middle of 20 things running.

thanks!

---

### Post by Mr Black on 2005-03-27
have you tried typing in *ifup eth1*?

---

### Post by ola on 2005-03-27
You can try to resolve the IP again with:
```

sudo dhclient eth1

```

or you can restart the networking with:
```

sudo /etc/init.d/networking restart

```

---

