---
title: "USB installing Ubuntu Remix on HP mini"
date: 2009-07-04
forum: Installation &amp; Upgrades
---

### Post by ghepardolesto on 2009-07-04
I have a HP 2140 with Windows XP Home and I wanted to install ubuntu remix on it.
I followed all the required steps described in the installation guide but when I select
booting from the USB stick, it gives me back the line "boot error". striking the space bar
a couple times I also got this message: :Non-system disk or disk error. replace and strike any key when ready"

Can anybody help me?? :(

thanks

---

### Post by earthpigg on 2009-07-04
what method, *specifically*, did you use to put ubuntu on the usb stick?

---

### Post by Ptero-4 on 2009-07-04
You need to type
```

syslinux /dev/*sdb*

```
replacing sdb with your stick's block device (sdb if you got a SATA HD, sda if you got an IDE HD).

---

