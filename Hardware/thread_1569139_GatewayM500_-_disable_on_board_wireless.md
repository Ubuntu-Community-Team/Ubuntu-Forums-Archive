---
title: "GatewayM500 - disable on board wireless"
date: 2010-09-06
forum: Hardware
---

### Post by SmokinRK on 2010-09-06
Hi there,

I installed Ubuntu on a Gateway M500 and everything went well as far as sound and video etc..

Can someone help me out with disabling the onboard wireless in Ubuntu and steering me in the right direction to configure a PCMCIA wireless card? 

I looked in the bios on the laptop for the option but it doesn't exist.

Thanks! in advance for your advice/assistance.

---

### Post by silbak04 on 2010-09-06
It should be somewhere in your bios, but you can also try editing your blacklist file which should be located in:

```

sudo gedit /etc/modprobe.d/blacklist

```

and in that file you'll just 
```
 
blacklist whatever_you_don't_want

```

or if that doesn't work...try using

```

rmmod wireless_you_don't_want

```

Hope this helps!

---

