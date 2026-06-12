---
title: "Network Manager Issues"
date: 2006-09-24
forum: Hardware &amp; Laptops
---

### Post by Leebobs on 2006-09-24
Hello All,

I have a fresh install of Ubuntu 6.06.1 on my Dell Inspiron 6000 (with internet connected via my eithernet port).

I install network manager through apt and reboot - the system starts and then tells me that

"Network Manager cannot find required resources"

Anyone got a fix for this?

---

### Post by xyz on 2006-09-24
According to this bug report
[https://launchpad.net/distros/ubuntu/+source/network-manager/+bug/45609](https://launchpad.net/distros/ubuntu/+source/network-manager/+bug/45609)
it was solved with this command line. Hope it works for you,too.

```
sudo gtk-update-icon-cache -f /usr/share/icons/hicolor/
```

---

### Post by Leebobs on 2006-09-24
xyz,

Many thanks for that, that fixed it!

What a silly bug! I hope this is fixed in Edgy & 6.06.2

Andy

---

