---
title: "AMD Radeon HD 8400, Ubuntu will not play nicely with it"
date: 2014-02-13
forum: Hardware
---

### Post by rolltide101x on 2014-02-13
I bought this PC
[http://www.bestbuy.com/site/15-6-laptop-4gb-memory-750gb-hard-drive/3782018.p?id=1219093517478&skuId=3782018&st=hp-laptops-118207&cp=1&lp=1](http://www.bestbuy.com/site/15-6-laptop-4gb-memory-750gb-hard-drive/3782018.p?id=1219093517478&skuId=3782018&st=hp-laptops-118207&cp=1&lp=1)


Ubuntu will not boot without the "nomodeset" parameter. I installed Ubuntu using "nomodeset" and have to add it to grub for it to boot now that it is installed. But I think there is an issue with the driver for the AMD Radeon HD 8400 because the effects are going slow and the PC stutters while playing 1080p video which works fine in Windows 8. I have Legacy mode enabled on my bios and disabled fast startup. Any ideas? 

This is by far the most annoying issue I have had out of Ubuntu ever. (Have/had Ubuntu on about 6 PCs)


I going to try the FGLRX drivers to see if that improves things. Will post back

---

### Post by open2reason on 2014-02-13
I expect that the Radeon HD 8400 may not be supported

> **Unsupported Chips**

 For  the very latest cards, open-source driver support is not always  instant. The following cards require a newer version of the driver than  what's found in Ubuntu 13.04/Raring's repository, but should be  supported by the time Ubuntu 13.10/Saucy is released. 
OLAND                       Radeon HD 8xxx series
HAINAN                      Radeon HD 88xx series
RICHLAND                    Radeon HD 8xxxG series via [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

I also had troubles (12.04.4) with my unsupported Radeon chip [AMD/ATI] Kabini [Radeon HD 8330] and things were made better by as you suggested downloading via the System Settings > Additional Drivers tab.

All the best with your endeavours.

---

### Post by mastablasta on 2014-02-13
for the newish cards use proprietary drivers (fglrx) to get reasonable perfomance. Opensource driver is not there yet. though it will get improvements in 14.04 version. 

if you dont' want to wait and want to use opensource drivers then use a PPA

---

### Post by Mark Phelps on 2014-02-13
I recently switched to a Radeon R7 240 (HD 8500) and discovered that the default Radeon drivers didn't work anymore without "nomodeset" being set on boot.

However, I was able to install the latest Catalyst Beta 14.1 drivers by downloading the file from AMD and running it.  Now, I get both screens back and full resolutions on each, and don't need "nomodeset".

---

### Post by rolltide101x on 2014-02-14
The fglrx drivers work much better though still not as good as win8. 1080p works now :)

---

