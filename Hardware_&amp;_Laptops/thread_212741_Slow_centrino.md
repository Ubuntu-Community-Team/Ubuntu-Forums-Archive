---
title: "Slow centrino"
date: 2006-07-10
forum: Hardware &amp; Laptops
---

### Post by djoelsson on 2006-07-10
Hi everyone,

I just purchased a Toshiba satellite laptop with a core duo centrino chip.  I installed Dapper and everything runs smoothly exept that that I don't have any power management features (processor scaling, screen dimmer etc) and my wireless connection is SLOW.  It runs at about 1/10 the speed it does in windows.

It connects fine, so I know the driver works.  I'm thinking it has something to do with the lack of power management.  I.e. is it possible that the wireless power is ratcheted way down which causes the slowdown problem?  

I've done all the normal troubleshooting stuff (uninstalling driver, using ndiswrapper (didn't work), googling like crazy) but I can't figure it out.  I've resorted to using a PC card adapter instead.  It runs at normal speed, but kills the battery life.

Anyone else have similar problems with a centrino?

Thanks,
Dan

---

### Post by Paerez on 2006-07-10
I have not experienced this on my centrino, but you can disable wireless powermanagement by running:
```
# sudo iwconfig eth1 power off
```
assuming eth1 is your wireless device. To check the devices, just run:
```
# sudo iwconfig
```
to show them all, then you'll know which name to put in the command. This will run your wireless at full blast (hopefully :D)

---

