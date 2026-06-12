---
title: "Laptop stops using AC"
date: 2006-11-30
forum: Hardware &amp; Laptops
---

### Post by midna on 2006-11-30
I never had this problem with dapper, but with edgy it just seems to be getting worse and worse as time goes by. When I'm using my laptop and plug in the ac adapter, sometimes ubuntu registers that and sometimes it doesn't. Rather annoying when I'm working and have only 3% power. I have to shutdown and than the laptop knows its plugged in, except, I don't even have to move the cord when rebooting. !?

Lets say ubuntu is using ac. Sometimes it will just stop and go to battery power only. Doesn't matter if the batter is 5% or 98%. It's completely random. I have a zt3000, running ubuntu edgy. I have no idea what to do.

Thanks

---

### Post by Tilex on 2006-12-01
It may not be related with ubunu.  I once had this problem with my laptop: when my system was on, the battery stopped recharging, and when I shutdown, it would charge (i.e use AC).  

My problem was physical.  The pin in the laptop where you plug the AC cord was semi-broken so I had to fix it.  As if the pin wasn't completely on the DC board so when the system was on, the power wasn't sufficient for the system, but when it was off, the little power that could get in was enough to recharge the battery.

Is the AC cord (the end that fits in the laptop) very hot when recharging?  If yes, that may be the problem because there is very much power dissipated through heat because it does not all get to the computer.

---

### Post by zgornel on 2006-12-01
Do a lsmod and check for the *ac* module.

---

### Post by midna on 2006-12-01
lsmod includes ac and I'll break open the case to check the pins on the power connections. My warranty is up anyway ;)

---

