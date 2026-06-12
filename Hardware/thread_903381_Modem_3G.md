---
title: "Modem 3G"
date: 2008-08-28
forum: Hardware
---

### Post by zeevpoli on 2008-08-28
I have a HP pavilion dv6680 working fine (without fingerprint if you could help with this too :) ).
I have Sierra Wireless AirCard 880E - modem for 3g (maybe 3.5G, if this matter) internet, work with a cellphone Sim Card and give me the "power" to connect internet anywhere anytime...
But i have no idea how to use it on linux (ubuntu) on windows i have only to connect him to the computer and the drive install it self, i think in mac os too, but it has no driver in linux, i asked Sierra and have no answer...
So what i need is a drive or how to use it on linux...
Thanks!

( [http://www.sierrawireless.com/product/AC880E_AC881E.aspx](http://www.sierrawireless.com/product/AC880E_AC881E.aspx) )

---

### Post by kagashe on 2008-08-28
> **zeevpoli said:**
> I have a HP pavilion dv6680 working fine (without fingerprint if you could help with this too :) ).
I have Sierra Wireless AirCard 880E - modem for 3g (maybe 3.5G, if this matter) internet, work with a cellphone Sim Card and give me the "power" to connect internet anywhere anytime...
But i have no idea how to use it on linux (ubuntu) on windows i have only to connect him to the computer and the drive install it self, i think in mac os too, but it has no driver in linux, i asked Sierra and have no answer...
So what i need is a drive or how to use it on linux...
Thanks!

( [http://www.sierrawireless.com/product/AC880E_AC881E.aspx](http://www.sierrawireless.com/product/AC880E_AC881E.aspx) )Linux does not need any separate drivers. Is it connected to pci or usb?

Anyway, whatever it is. Please open a terminal and post the output of the commands here:
lspci
lsusb
dmesg | grep Sierra

kagashe

---

