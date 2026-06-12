---
title: "ATI Catalyst 9.3 download link?"
date: 2010-06-28
forum: Hardware
---

### Post by crazyfuturamanoob on 2010-06-28
I have tried 10.5 and 10.6, but they got texture problems in Spring (RTS). 
[COLOR="Silver"][s]I read that 9.3 should work, but where to download it? And is is possible to install it on Kubuntu 10.04?[/s]
[/COLOR]
EDIT3: [SIZE="4"]**SOLUTION: Use Catalyst 10.4. All textures work.**
Download link: [https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-10-4-x86.x86_64.run](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-10-4-x86.x86_64.run)[/SIZE]
[COLOR="Silver"]
[s]
EDIT:
Found 9.2: [https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-9.2-x86.x86_64.run](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-9.2-x86.x86_64.run)
And 9.3: [https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-9-3-x86.x86_64.run](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-9-3-x86.x86_64.run)
[/s]
EDIT2: I couldn't install 9.3:
```

arho@a91-156-166-231:~/Downloads$ sudo sh ./ati-driver-installer-9-3-x86.x86_64.run 
Created directory fglrx-install.Oc6371
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.593...........................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================

Error: ./default_policy.sh does not support version
default:v2:x86_64:lib32::none:2.6.32-22-generic; make sure that the version is being
correctly set by --iscurrentdistro

Removing temporary directory: fglrx-install.Oc6371
arho@a91-156-166-231:~/Downloads$ 

```
[/COLOR]

---

### Post by andreselsuave on 2010-07-01
I am trying to install the 9.3 version and get the same error message :(

---

### Post by andreselsuave on 2010-07-01
Found the answer: 

Old ati cards are no longer supported for new versions of X. This means either you use the open driver or install an old version of your linux distribution. It's a pity :/

[Look here]("http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Installing_Proprietary_Drivers_a.k.a._Catalyst.2Ffglrx")

---

### Post by crazyfuturamanoob on 2010-07-02
I have a mobo-integrated Radeon HD 4290. It was the first video card I bought from ATI, and will be the last one too. :|

All my other PC's with Nvidia GPU work fine. I don't even have to manually download and install the drivers because Jockey does it!

Edit: I tested many drivers and 10.4 works. :D

---

