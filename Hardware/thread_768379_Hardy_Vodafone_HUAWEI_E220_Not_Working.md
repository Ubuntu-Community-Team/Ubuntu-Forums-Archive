---
title: "Hardy Vodafone HUAWEI E220 Not Working"
date: 2008-04-26
forum: Hardware
---

### Post by atasaRossios on 2008-04-26
Hi just wanted to ask if there is anyone that uses Vodafone Mobile Card HUAWEI E220.
This is a very long story for me because I am trying to solve this since September 2007.
I have installed vodafone-mobile-connect-card-driver-for-linux_1.99.17_i386.deb in Gutsy but my device was recognized as a Cd-Rom.
I have try to workaround this issue with various howto's but no luck.
Now I installed the same package on Hardy the device is not recognized as a Cd-Rom any more, but I always get the Error:
*run_program: '/usr/sbin/huaweiAktBbo' abnormal exit*

Anyone....

---

### Post by ingManiac on 2008-04-27
Hello!
I use Vodafono-Mobile-Connect-Card-Driver for linux.
Beta 2.0 with the Huawei E220 and it works fine.
I did not need any special settings worked right out of the box.
I also used 1.99 with gutsy and feisty worked also without problems.
The only thding that changed is in feisty and gutsy i had the virtual CD-drive of the modem on my Desktop when i plugged in the E220.
In Hardy it does not appear.

Hope u can use it too, it's a great Software.

From time to time i have little trouble with vodafone soft, and i have to restart system with modem plugged in on startup and it runs and sometimes i have to plug it in after system started, but most of the time it doesn't matter if it is plugged in on startup or afterwards!?
Maybe a little Bug.

---

### Post by mormor on 2008-04-28
Problems with E220 to start with to, but the drivers provided by vodafone worked right off install in ubuntu 7.10 for me, and just sucsessfully installed the 2.0 beta driver for Heron and its up and working. (for heron I needed to download some python packages, but that went along pretty easily.

Just google: Vodafone mobile connect linux drivers, or follow the link in my signature. : )

---

### Post by atasaRossios on 2008-04-28
thanks for the reply guys...
I will try the beta version also.
Did any of you try the stable version?
In hardy also the package downloaded and installed some extra packages like python-twisted etc.
It also adds some udev rules.
Once again what happens is that i get a message that cannot initialize the modem. 
Network manager also is connected to network via wlan0.
If any of this rings a bell to you.
Once again thanx

---

### Post by atasaRossios on 2008-06-30
Finally go it working with the Beta 3 Version without installing any extra package.
The only thing is to add the users you want to use this service to the vmc group.

Cheers

---

