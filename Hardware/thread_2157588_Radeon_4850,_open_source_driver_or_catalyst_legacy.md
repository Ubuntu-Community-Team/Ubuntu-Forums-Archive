---
title: "Radeon 4850, open source driver or catalyst legacy?"
date: 2013-06-26
forum: Hardware
---

### Post by gimchicoffee on 2013-06-26
Please help me on this. This is my second radeon graphics card I've had to deal with in Ubuntu. I eventually got the first one on a laptop to kind of work for some games, but after a ton of purple screens/painful digging to return functionality of the OS. I've just got a new computer which unfortunately has a Radeon HD 4850 and am trying to get the catalyst 12.6 driver to work with it in Ubuntu 11.04. It wouldn't install properly in 12.04 so I went back to 11.04 like I was using on the laptop. I installed it one time and got a purple screen on reboot. I'm too tired of trying to figure this out on my own... So, what is  your opinion on the open source driver? Will it be functional enough to play 2005-2008 era games) and not crash my system constantly?

---

### Post by Mark Phelps on 2013-06-26
If you were running 12.04.2, that AMD driver would not install as the driver conflicts with the X-server version in Ubuntu versions 12.04.2 and newer.

However, it should work with 11.04 -- you might try checking in the Video section to see what others have reported on this.

As to the open-source driver, it's not designed with Gaming in mind, so while it does provide some acceleration, you're not going to get the hardware acceleration needed for Gaming with decent fps rates.

---

### Post by Yellow Pasque on 2013-06-26
> However, it should work with 11.04
Running 11.04 is not a good option. If the main purpose of the machine is gaming, then install Ubuntu 12.04.1 and Catalyst 13-1 legacy driver.

> Last edited by QIII; 11 Hours Ago at 12:26 AM. Reason: asterisks are not a way to get around language filters. 
:P

---

