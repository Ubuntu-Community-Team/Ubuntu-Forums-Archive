---
title: "hp mini 2133 wireless"
date: 2009-10-29
forum: Installation &amp; Upgrades
---

### Post by nathang1392 on 2009-10-29
just downloaded and installed karmic on an hp mini 2133 and it cant connect to my wireless network. is this common, and can anyone point me to a solution?

---

### Post by zalberico on 2009-10-29
I found this site that might help you
[https://wiki.ubuntu.com/LaptopTestingTeam/HP2133](https://wiki.ubuntu.com/LaptopTestingTeam/HP2133)

Don't have any personal experience with it though.

Good Luck.

---

### Post by nathang1392 on 2009-10-29
its actually my friends computer and i have internet access and he doesnt so im trying to find something that i can put on a usb drive and use that to install. any ideas?

---

### Post by nathang1392 on 2009-10-30
if i install ndis wrapper and this [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php) would it work?

---

### Post by BenRitchie on 2009-10-30
> **nathang1392 said:**
> just downloaded and installed karmic on an hp mini 2133 and it cant connect to my wireless network. is this common, and can anyone point me to a solution?

I have a 2133 and the upgrade was flawless for me, wireless worked out of the box with 8.04->9.10 (unlike the display, which took some hacking originally). So there shouldn't be anything special required to get it to work

---

### Post by nathang1392 on 2009-10-30
i did a dualboot with windows and after install the wireless cant be found. if i go on the live cd and install ndiswrapper it will then recognize the wireless card, but after i boot back into the hard drive partition it is no longer found

---

### Post by ferebee on 2009-11-04
> **nathang1392 said:**
> i did a dualboot with windows and after install the wireless cant be found. if i go on the live cd and install ndiswrapper it will then recognize the wireless card, but after i boot back into the hard drive partition it is no longer found

This worked for me, but your mileage may vary - when I was using the live usb there were two drivers available under System> Hardware Drivers - on my mini I chose the STA driver, as that's the one I'd used in Jaunty. (Following advice from [here]("http://www.linlap.com/wiki/hp+2133"). No updates on there for Karmic yet. Not many threads at the [HP Mini Guide Forums]("http://www.hpminiguide.com/forums/") yet either.)

On install, there was nothing in System> Hardware drivers at all, and wireless didn't work. I mounted the live usb and found the driver on the install media in the Pool> Restricted folder and installed that .deb package, rebooted and we were in business.

---

