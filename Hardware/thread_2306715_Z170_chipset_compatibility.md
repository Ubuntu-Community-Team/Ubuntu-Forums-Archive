---
title: "Z170 chipset compatibility"
date: 2015-12-18
forum: Hardware
---

### Post by IJM on 2015-12-18
Been reading mixed messages re the compatibility of the new Z170 chip sets (skylake intel processors) and Ubuntu.  Apparently there is a problem with 14.04 LTS, which should / could be solved by upgrading to 15.10   There are possible solutions using the latest kernals, but it still seems very vague and uncertain.  So two questions - has anyone tried the new chip set with 14.04 and the latest upgrades, or anyone tried 15.10 'out of the box'.  Thanks

---

### Post by Yellow Pasque on 2015-12-18
If you want to run an LTS with a brand new Z170 system, it would seem logical to wait for 16.04. A lot of times you can hack in newer kernels and other updates to an older LTS, but that can be intimidating and difficult for less advanced users, especially if the guides are outdated or confusing.

In the meantime, you can run 15.10 and then try an upgrade to 16.04. Back up your personal data in case it doesn't go well and you have to do a reinstall (or maybe you just want to do a fresh install anyway).

---

### Post by oldfred on 2015-12-18
Another thread on same issue:
       Best Ubuntu version for new Z170 motherboards /w Intel video? Oct 2015
[http://ubuntuforums.org/showthread.php?t=2292521](http://ubuntuforums.org/showthread.php?t=2292521)

              [http://askubuntu.com/questions/705796/msi-z170a-gaming-m5-with-linux-dual-boot](http://askubuntu.com/questions/705796/msi-z170a-gaming-m5-with-linux-dual-boot)
    
 Xeon Skylake Users May Run Into Display Problems With Current Distributions Dec 2015
[http://www.phoronix.com/scan.php?page=news_item&px=WKS-GT2-No-Modeset](http://www.phoronix.com/scan.php?page=news_item&px=WKS-GT2-No-Modeset)
Intel's Skylake Audio Firmware Lands
[http://www.phoronix.com/scan.php?page=news_item&px=Intel-Skylake-Audio-Firmware](http://www.phoronix.com/scan.php?page=news_item&px=Intel-Skylake-Audio-Firmware)
[http://www.phoronix.com/scan.php?page=news_item&px=Intel-SKL-BXT-Firmware-Blobs](http://www.phoronix.com/scan.php?page=news_item&px=Intel-SKL-BXT-Firmware-Blobs)
Skylake Intel Core i5 6500: A Great Skylake CPU For $200, Works Well On Linux, 4.3 kernel  for best graphics
[http://www.phoronix.com/scan.php?page=article&item=intel-i5-6500&num=1](http://www.phoronix.com/scan.php?page=article&item=intel-i5-6500&num=1)
Skylake needs this boot parameter:  i915.preliminary_hw_support=1
[http://www.phoronix.com/scan.php?page=news_item&px=Intel-SKL-Prelim-Support](http://www.phoronix.com/scan.php?page=news_item&px=Intel-SKL-Prelim-Support)

---

