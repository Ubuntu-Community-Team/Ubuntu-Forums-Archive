---
title: "[TIP] Use HPLIP for Hewlett-Packard Hardware"
date: 2009-09-07
forum: Hardware
---

### Post by e.pequeno on 2009-09-07
This is meant to be a tip that came from experience with two bits of HP hardware, a laserjet printer and and an all-in-one deskjet.

When I have installed ubuntu distros in the past (from hardy heron on up) ubuntu is good about detecting the hardware and finding the correct models and attempting to install the necessary drivers.

The laserjet printer the drivers that ubuntu tried to use simply did not work and so it sat unused as a result.  For the deskjet ubuntu was able to find a driver that gave me the printing function but did not recognize the scanner.  I tried to use xsane to scan a document and xsane returned an error saying that no scanning devices could be detected. 

So I did a bit of searching and found a suggestion someone had posted here about another hp product which would not install directly.  They suggested to use the latest [HPLIP]("http://hplipopensource.com/hplip-web/index.html") software.  

HPLIP was excellent and came with very detailed instructions on how to install and run the software.  Now both devices work with full functionality. Generally speaking all you have to do is tell hp the details of the hardware you are trying to install and the version of linux you are trying to install to and run the provided shell script and the installer will guide you through the rest painlessly.  After that you are left with a cli program "hp-setup" which will easily install hp hardware and ensure the latest drivers and plugins available from HP are used.  

In my opinion this method is far more reliable than ubuntu's default behavior of installing device drivers.

Details:
Linux 2.6.28-15-generic #49-Ubuntu SMP Tue Aug 18 18:40:08 UTC 2009 i686 GNU/Linux
[HP Deskjet F4480 All-in-One Printer, Scanner, Copier]("http://www.shopping.hp.com/store/product/product_detail/CB745A%2523B1H/1;HHOJSID=RBs6KlgLLckZFwqdcZp1gHw1vrQ4npVGh1PN2KtNNqBLm2dGvgxd!-2058330213?jumpid=in_r329_personalization/browse1/suppies_model_PDP") (CB745A#B1H)
[HP LaserJet 1018 Printer]("http://h10010.www1.hp.com/wwpc/us/en/sm/WF10a/18972-18972-3328059-14638-3328066-1814092.html?jumpid=reg_R1002_USEN") (CB419A) *discontinued

---

