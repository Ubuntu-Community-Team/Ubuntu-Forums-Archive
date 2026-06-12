---
title: "Choppy mouse at startup and some times"
date: 2012-08-31
forum: Hardware
---

### Post by galinette on 2012-08-31
Dear all,

I installed recently ubuntu on a Lenovo R400 laptop (Intel graphics version) on which I replaced the HDD by an Intel 330 SSD.

The mouse cursor movement sometimes becomes very choppy, with strong delay and totally unsmooth movement, barely usable. This happens mostly at startup (gdm and just after opening a session) and also at some other times (without identifiable logic behind it). This happens with both the trackpoint and the touchpad.

Do someone has any idea?

Thanks!

Etienne

---

### Post by Colo993 on 2012-08-31
galinette,

I have also seen the same behavior on my Dell laptop running Ubuntu 12.04.  I have an Nvidia chipset and have tried various graphics drivers thinking this was causing the issues.  So far the only thing that helps is to reboot.  After the reboot the mouse responds normally.  I'm running Gnome but have seen the exact same behavior on Unity.

I've checked my ~/.xsession.errors and /var/log/syslog for clues but haven't found anything yet.  Maybe something to do with Compiz?

Colo993

---

### Post by iFritz on 2012-11-07
Hey Folks,

same issue here. Its a R400 with a swapped HDD of a Lenovo SL500
with Ubuntu 12.04 on it. Plugged the HDD(Ubuntu/SL500) into the R400 and it looked like it runs out of the box. Except for the mouse and keyboard. Same things happen. Mouse slows down randomly and keyboard then at the same time or a bit later.
It takes a while and evrything is back fast and usable.
Can't find anything in dmesg. Syslog doesnt load kernel.log etc.

Any hints?

---

