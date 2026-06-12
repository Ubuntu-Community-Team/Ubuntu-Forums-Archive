---
title: "Fujitsu Lifebook A3040 USB, Ethernet and Wireless issues"
date: 2007-07-10
forum: Hardware &amp; Laptops
---

### Post by gaten on 2007-07-10
I have a Fujitsu Lifebook A3040 with Feisty installed. The install went just fine, everything worked out great. Except when I try and use it.

Ethernet does not work. DHCP or static, irreguardless of what settings I use. My router does not even see any DHCP requests, which leads me to believe that the card does not work at all under Ubuntu. The only error I see is from dmesg, which reads:
```
ADDRCONF(NETDEV_UP): eth0: link is not ready
```

Yes, I've tested various cables and so on, it's not the cable its the OS. And it works fine in Windows and with Backtrack 2 LiveCD. 

Wireless also does not work, I can't see or connect to any wireless AP. 

And last but not least, USB does not even work. I can't plug in my thumb drive and transfer ANYTHING over. Dmesg does not even report seeing the device plugged in, let alone be able to use it.

I'm looking for any help you can give. I regret purchasing this laptop now (as it just sucks in general), but it's too late now. Thanks in advance.

Oh, and yes I know it's not on the compatibility list.

---

