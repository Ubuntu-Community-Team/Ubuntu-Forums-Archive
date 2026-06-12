---
title: "Ethernet Help"
date: 2006-04-26
forum: Hardware &amp; Laptops
---

### Post by xmonkey on 2006-04-26
I just installed Breezy Badger on my Toshiba Satellite laptop and everything works fine except I can't access the internet. My laptop has a modem, ethernet and wirless (I use ethernet mainly) All three show up in the network place and my ethernet is set at DHCP, I can ping out to a website, It says i'm sending and recieving packages but mozilla/email/chat won't work. Please help me, I'm going through internet withdraw!  ](*,) 

Thanks!

---

### Post by mips on 2006-04-27
Try disabling IPv6.

```
sudo mv /lib/modules/$(uname -r)/kernel/net/ipv6/ipv6.ko /lib/modules/$(uname -r)/kernel/net/ipv6/ipv6.ko.bak

sudo depmod -a
```

---

### Post by xmonkey on 2006-04-27
didn't work, said no such file or directory. thanks for the idea though, anything else I can try?

---

### Post by mips on 2006-04-28
[QUOTE=xmonkey]didn't work, said no such file or directory. thanks for the idea though, anything else I can try?[/QUOTE]

Sure, you should have one unless you renamed it already ?

---

