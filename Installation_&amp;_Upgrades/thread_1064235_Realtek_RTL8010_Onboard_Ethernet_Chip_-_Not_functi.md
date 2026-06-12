---
title: "Realtek RTL8010 Onboard Ethernet Chip - Not functioning after upgarde to 2.6.27-11"
date: 2009-02-08
forum: Installation &amp; Upgrades
---

### Post by james.walmsley on 2009-02-08
I know other have reported this problem, but I don't think it's been properly explained, or understood. Essentially the upgrade from Kernel 2.6.27-7 to 2.6.27-11 has stopped my ethernet working.

Even when I boot back into 2.6.27-7 it will no longer work. I cannot get a dhcp!

I've just spent a day recompiling the latest stable kernel from Kernel.org. 2.6.28-4 It seems to solve some problems with the driver. Atleast there's not a huge packet drop count when looking at ifconfig.

Some people say they fixed this with the bios, unfortunately they didn't explain what they changed. Others also offered compiled versions of the realtek driver. This was also no good, because I also compiled the latest source, and blacklisted the other realtek drivers, and still nothing is fixed.

Sorry I can't provide any logs because I have no wireless, and I have to write this from Windows.

I'm a bit dissappointed with Ubuntu, I just came from OpenSUSE and I have to say, their hardware support seems to be top-notch. My ethernet on the same laptop never broke from kernel updates. 

James

---

