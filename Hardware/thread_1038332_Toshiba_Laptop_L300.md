---
title: "Toshiba Laptop L300"
date: 2009-01-12
forum: Hardware
---

### Post by prbrough on 2009-01-12
I have a brand new Toshiba L300 dual core laptop onto which I have installed Linux Ubuntu from a disc which came with my "Beginning Linux Ubuntu" book. No other OS is installed. After completing the installation the reboot failed with a Busy Box "initramfs" message. The book did not cover this one! I have been referred to the October 2008 thread on this topic where it was suggested that I disable the LAN setting in BIOS to overcome an identified problem with the ethernet connection which causes the error on this model of laptop. This worked and Ubuntu loaded. The same thread then suggested updating from 8.04 to 8.04.1 where apparently the problem does not re-occur. I cannot update via my new laptop as I cannot connect to the internet with the LAN disabled. Presumably I have to download the update somehow via another computer, but where do I find it? I have loooked on all the Ubuntu support pages but I cannot find 8.04.1 - only 8.04 LTS and 8.10. Can anyone direct me please? And do I have to download to a cd as an ISO image? You will gather that I am keen to learn about Linux but the technical side comes hard to a pavlovian windows user!

---

### Post by sigixv on 2009-05-31
I have the same laptop, although it came loaded with vista.

In ubuntu 8.xx i had problems with the realtech drivers (lan & wifi). I also had to disable LAN in BIOS and enabling both at the same time wasn't possible.

If you install 9.04 all of these problems are over and everything should work out of the box without any extra configureing. (at least for me it did)
Remember to turn on LAN in the BIOS before you install it.

The intel graphic drivers hower are blacklisted. If you want to enable compiz (needed for desktop effects) you have to disable the driver-check. 

```
mkdir -p ~/.config/compiz/ && echo SKIP_CHECKS=yes >> ~/.config/compiz/compiz-manager
```This however is not guaranteed to be stable, but i did not yet encounter any problems so far...

---

