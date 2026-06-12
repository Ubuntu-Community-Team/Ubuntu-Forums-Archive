---
title: "hp pavilion dv9700 wifi works but!!!!!"
date: 2008-09-02
forum: General Help
---

### Post by Priest.Lucard on 2008-09-02
I installed the drivers for the WiFi card in the laptop and it does work but each time i boot the system i have to go into a terminal and type this.

cd /
cd home
cd lucard
cd hybrid_wl
sudo make -C /lib/modules/2.6.24-21-generic/build M=`pwd` clean
sudo make -C /lib/modules/2.6.24-21-generic/build M=`pwd`
sudo modprobe ieee80211_crypt_tkip
sudo insmod wl.ko

Then the WiFI works. 
Does anyone know how i can make it load this each time i boot up so i do not have to keep going in to the terminal.

Ubuntu 8.04 on a 32 bit install
Broadcom Corporation - BCM4322
[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

---

### Post by malachi1990 on 2008-09-02
Have you tried Ndiswrapper?  From what I understand, the linux drivers from broadcom have serious problems, so Ndiswrapper will let you use the windows ones.  Heres one how-to from the forums.

[http://ubuntuforums.org/showthread.php?t=870086&highlight=ndiswrapper+broadcom](http://ubuntuforums.org/showthread.php?t=870086&highlight=ndiswrapper+broadcom)

---

### Post by Priest.Lucard on 2008-09-02
I can do that but I would rather use the Linux drivers if I can. It does work I just need to run the set of command each time I start up the computer. Is there a way to have it load the drives on boot up so I will have to type this list of command each time?

---

