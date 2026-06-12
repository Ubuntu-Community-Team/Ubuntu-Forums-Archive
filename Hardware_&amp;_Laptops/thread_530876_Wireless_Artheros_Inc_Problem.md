---
title: "Wireless Artheros Inc Problem"
date: 2007-08-20
forum: Hardware &amp; Laptops
---

### Post by Fabio Charry on 2007-08-20
Hi Everybody,

Once again a wirless problem, but belive me there isn`t formus or post about this issue that could help me, I`v spend many hours tryin`to find a solution but it was not possible.

I have an IBM ThinkPad A22m, & a Belkin F5D7010 Wirless G Notebook Card. All forums talk about a Broadcom Chipset, I try to install all available firmware and stuff, but It allways shows Ath01 Artheros Inc Device Unknown.

If some of you my friends have different info about it I really apreciate it.

Best regards & peace for all of you :D:)

---

### Post by ntlam on 2007-08-21
[http://ubuntuforums.org/showthread.php?t=187004](http://ubuntuforums.org/showthread.php?t=187004)

---

### Post by ntlam on 2007-08-21
you may want to remove madwifi first if you did try installing it

---

### Post by arranmc182 on 2007-11-19
you can try going to [http://linuxwireless.org/](http://linuxwireless.org/) and downloading the Linux wirless drivers from there they worked 100% for me and works a lot better than ndiswrapper as it puts the drivers right in to the mian kernel and its all verry simple to install.

here is just some of the drivers u will get

b43/b43legacy (Broadcom chips)
ath5k (Atheros devices)
adm8211 (ADMtek devices)
madwifi (Atheros devices)
p54 (Intersil chips)

and there are even more drivers built in all you have to do us install it and linux will detect what driver is needed if you have compatable hardware

---

### Post by slomat on 2007-12-12
Latest ath5k ( OpenHAL !) integrated with kernel 2.6.23 with all prepatch working perfecty with thi laptop :)))
> **arranmc182 said:**
> you can try going to [http://linuxwireless.org/](http://linuxwireless.org/) and downloading the Linux wirless drivers from there they worked 100% for me and works a lot better than ndiswrapper as it puts the drivers right in to the mian kernel and its all verry simple to install.

here is just some of the drivers u will get

b43/b43legacy (Broadcom chips)
ath5k (Atheros devices)
adm8211 (ADMtek devices)
madwifi (Atheros devices)
p54 (Intersil chips)

and there are even more drivers built in all you have to do us install it and linux will detect what driver is needed if you have compatable hardware

---

