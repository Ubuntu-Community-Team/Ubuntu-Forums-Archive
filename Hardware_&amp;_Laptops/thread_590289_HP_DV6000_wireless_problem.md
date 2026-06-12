---
title: "HP DV6000 wireless problem"
date: 2007-10-24
forum: Hardware &amp; Laptops
---

### Post by Z_o-s-o on 2007-10-24
Hey I'm having a slight problem with my Broadcom 43xx wireless card under Ubuntu Studio 7.04.

For a while, I had everything working just fine via Ndiswrapper and the bcm4xx driver, but I ditched 7.04 for Studio 7.10, which was very buggy.

After all of that, I ended up reinstalling Ubuntu Studio 7.04, and reconfigured everything the way it was before, and everything was working fine until yesterday after some updates (don't remember what they were, but now I'm seeing some kernel options I ever saw before).

Now the wireless card doesn't even show up in lspci like it used to. It seems that the card is "gone". 

I'm using the "easy way" installer to install the driver and ndiswrapper, and before, when installing, it told me "incompatible chip set found" which is fine, as it means I had use the ndiswrapper install method, but now it's not detecting the chipset at all.

Thanks!

---

### Post by Cyber-J on 2007-10-24
Until I discovered a working Broadcom firmware file at:

[http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o](http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o)

Using Ndiswrapper was my only choice to get wireless working but now I can use the restricted drivers (bcm43xx-fwcutter) for a change. I downloaded that firmware and I now keep it in a safe place. Then I just tell the installer where to find it when installing the restricted drivers. I only need to do this during the installation and then after that - working bcm43xx wireless drivers without Ndiswrapper. =)

---

### Post by Z_o-s-o on 2007-10-24
I wish I new how to use what you provided.

It also looks like my /etc/network/interfaces file is gone?

---

### Post by Z_o-s-o on 2007-10-24
Bump

I really don't want to have to reinstall again...

---

