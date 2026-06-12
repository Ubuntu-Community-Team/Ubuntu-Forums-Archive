---
title: "Broadcom BCM4313"
date: 2011-05-07
forum: Hardware
---

### Post by swaroop933 on 2011-05-07
Hi Everyone,

I am new to Ubuntu/Linux. I installed Ubuntu 11.04 on my Lenovo B560. My wireless STA driver is appearing to be activated and in use but I can't use Wireless connection... Can any one help

I have "Wireless is disabled by hardware switch" but my hardware switch is ON... Pls help

---

### Post by yablokoff on 2011-06-11
Maybe this answer will be out-of-date, but still (;

Had the same trouble in my Lenovo B560 with Ubuntu 11.04 - standart broadcom driver from synaptic was causing the "Blocked by hardware switch" state and nothing seemed to fix it.

The device is Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727].

Finally got to that steps:

[LIST=1]
[*]- find out what module is supposed to be appropriate - [http://wireless.kernel.org/en/users/Drivers/b43]("http://wireless.kernel.org/en/users/Drivers/b43")
[*]- download and compile driver from broadcom-sta-source like it's described here [http://community.linuxmint.com/tutorial/view/218]("http://community.linuxmint.com/tutorial/view/218")
[*]- after that "Enable Wireless" checkbox appeared, but wireless connection couldn't be set up because of "Wireless is disabled". That was caused by acer-wmi module. I switched it off by
```
sudo modprobe -r acer-wmi
``` 
and then added it to boot blacklist here:
```
echo "blacklist acer-wmi" >> /etc/modprobe.h/blacklist.conf
```
[/LIST]

Now it works almost seamlessly, with just a small delay of initial connection!

---

### Post by coffeecat on 2011-06-11
Broadcom 4313 wireless. I thought I'd drop my experience in here as I keep coming across people who've been stymied by the STA driver with this device:

[http://ubuntuforums.org/showthread.php?t=1744983](http://ubuntuforums.org/showthread.php?t=1744983)

The Broadcom 4313 device **works out of the box** in 11.04 with the new default open source  brcm80211 driver. Unfortunately, this driver only works with three or four Broadcom chipsets, but the BCM4313 is one of them.

My advice to anyone with this device installing Ubuntu 11.04. Jockey (additional drivers) will pester you to install the STA driver. **Ignore it.** Also, when you install from the live CD/USB, do not tick the update while installing box. I believe this will sneak in the STA driver while you're not looking.

Do not install the STA driver with this chipset. From all that I have read, you will regret it.

---

### Post by yablokoff on 2011-06-13
Thanks a lot, somehow I missed it out!

Will try on my next installation

---

### Post by coffeecat on 2011-06-13
Good luck! :)

Also, are you going to be installing 32 or 64-bit?

---

### Post by garwyn on 2011-11-26
I may be a bit late to this party as well, but I know this is an ongoing issue; I had different problems/ fixes with two of the same Lenovo B series laptops with the lack of connectivity and it is a very important issue to resolve. I used two different fixes with two of the same machines. One worked only on machine #2, the other machine both fixes worked- just for experimentation. It is actually simple but I have seen some rather complex "solutions" that dont work consistently- or at all- at least for me.

Fix #1- I first totally agree with the "don't install the recommended driver" as coffecat wrote, then: install WICD, and COMPLETELY remove network manager-gnome. Blacklist any added or additional drivers such as B43*, etc., in the /etc/modprobe/blacklist.conf file. This will prevent having to do the "rfkill unblock all" nonsense in terminal every restart. (software and/or hardware blocks present).  Restart, open WICD and your connection list should appear. Pick yours, push "connect". That worked well.

  Fix #2 was to install (or keep) network manager, blacklist above, but ESPECIALLY the acer-wmi ("blacklist acer-wmi") in the same location (/etc/modprobe/blacklist.conf).. If you had WICD installed, make sure it is TOTALLY removed. Now you will be able to turn on the software switch without it snapping closed, and enter your "network name" (actually the SSID) and your passphrase into Network Manager. Your wireless should be recognized immediately. 
 Both fixes work, both work very well. As coffecat said, the broadcom 4313 works OUT OF THE BOX with both Ubuntu 11.04 and 11.10. (By the way, my first fix worked, it seems, easier on 11.04, where I had problems with that same fix after a few weeks- but that could have been my fault- so I used fix #2.) So DON'T INSTALL the STA driver when prompted- OR the 43-cutter (sp?) drivers, they are older and wrong also. Blacklist them as well, remove if installed. These cause many of the conflict problems.
 Hopefully, these suggestions will put this matter to rest once and for all. I know it is fairly widespread with Broadcom drivers, and not only Lenovo laptops. 

Cheers. Gary

---

