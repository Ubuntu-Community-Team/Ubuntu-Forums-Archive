---
title: "Wifi not working on Dell Vostro 1000 with 12.04"
date: 2012-10-06
forum: Hardware
---

### Post by gutam2000 on 2012-10-06
Dear Friends,

My wifi not working on Dell Vostro 1000 with 12.04. I have downloaded the propriety driver for the hardware Broadcom STA driver still its not working. However it is working with Windows7. Yesterday, a reparing guy had removed my hard drive and inserted his windows7 and it was working fine.

How can I activate wifi on my Vostro Dell 1000?

Thanks
Sridhar

---

### Post by ArmyJM on 2012-12-18
first run this code 

```
 sudo rfkill unblock all 
``` and reboot if still not working download and install firmware-b43-installer and b43-fwcutter from the software center or through apt-get.

```
 sudo apt-get install firmware-b43-installer b43-fwcutter 
```

 and run the first command again and reboot. all should work after that. 

reference [http://askubuntu.com/questions/125529/wireless-doesnt-work-on-a-broadcom-bcm4312](http://askubuntu.com/questions/125529/wireless-doesnt-work-on-a-broadcom-bcm4312)


p.s. this worked on my Vostro 1000 should be the same for you, all of my Fn-keys and keybinding work as they should.

---

