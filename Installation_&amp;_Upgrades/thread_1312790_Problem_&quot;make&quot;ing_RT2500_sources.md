---
title: "Problem &quot;make&quot;ing RT2500 sources"
date: 2009-11-03
forum: Installation &amp; Upgrades
---

### Post by stoyanmihaylov on 2009-11-03
I downloaded RT2500 sources and when I tried to make them - received:
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-14-generic'
  Building modules, stage 2.
  MODPOST 0 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-14-generic'
rt2500.ko failed to build!

I am using RT2500 from long time - may be since 8.04, and never had problems making and installing this module.
Current configuration is:
hardware: laptop MSI with 
Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)
Default driver works slow and bad. This is why I am using RT2500 - before from cvs, now from ubuntu repository.
Now I am with 9.10, and kernel - 2.6.31-14-generic
If I boot with older kernel (I keep it) - 2.6.28-16-generic, where I have previously installed RT2500 from cvs - then WiFi works without problems.
With module-assistant (following instructions in: [http://rt2x00.serialmonkey.com/wiki/index.php/Debian_rt2500_Howto](http://rt2x00.serialmonkey.com/wiki/index.php/Debian_rt2500_Howto)) - results are also same:

# Install module  
dh_installdirs lib/modules/2.6.31-14-generic/kernel/drivers/net/wireless 
Build modules 
/usr/bin/make KERNDIR=/usr/src/linux PATCHLEVEL=6 
make[2]: Entering directory `/usr/src/modules/rt2500' 
make[3]: Entering directory `/usr/src/linux-headers-2.6.31-14-generic'
Building modules, stage 2.
MODPOST 0 modules 
make[3]: Leaving directory `/usr/src/linux-headers-2.6.31-14-generic'
rt2500.ko failed to build!
make[2]: *** [module] Error 1 
make[2]: Leaving directory `/usr/src/modules/rt2500'
make[1]: *** [binary_modules] Error 2 
make[1]: Leaving directory `/usr/src/modules/rt2500'
make: *** [kdist_build] Error 2 

I will be happy if I could findout how to start make in verbose mode at least to find why I cant make.
I have headers, I have compilers etc... But obviously I miss something.

---

### Post by klinzter on 2009-11-14
hi all


i have the same problem... :8

---

### Post by stoyanmihaylov on 2009-11-15
What I did - now after start only lo interface is up.
Then - 
ifconfig wlan0 up
iwconfig wlan0 mode managed key restricted xxxxxxxxxxxxxxxxxxxxxxxxxx power off essid dd-wrt
dhclient wlan0
And this way my WiFi works with its "ubuntu" drivers - rt2500pci

---

