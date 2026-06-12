---
title: "Is Notebook MSI EX700X good for ubuntu??"
date: 2008-06-23
forum: Hardware
---

### Post by kapu on 2008-06-23
Notebook MSI EX700X

I want to buy this notebook but i don't know if all things work good on it.

page of shop: Notebook MSI EX700X

---

### Post by ukripper on 2008-06-23
never used these notebooks before but looking on their website [http://global.msi.com.tw/index.php?func=proddesc&prod_no=1317&maincat_no=135](http://global.msi.com.tw/index.php?func=proddesc&prod_no=1317&maincat_no=135)

---

### Post by kapu on 2008-06-23
> **ukripper said:**
> never used these notebooks before but looking on their website [http://global.msi.com.tw/index.php?func=proddesc&prod_no=1317&maincat_no=135](http://global.msi.com.tw/index.php?func=proddesc&prod_no=1317&maincat_no=135)


yeah, but there is nothing what can help me or is?

---

### Post by btermeli on 2008-06-23
I have MSI Megabook S260, it performs really good with Ubuntu, detected all hardware  automatically. But ur choice has Nvidia graphic card, mine  has Intel 915 (preinstalled on ubuntu 8.04).
For graphic card check the link;

[http://ubuntuforums.org/showthread.php?t=494041](http://ubuntuforums.org/showthread.php?t=494041)

Also Nvidia has Linux driver;

[http://www.nvidia.com/object/linux_display_ia32_100.14.09.html](http://www.nvidia.com/object/linux_display_ia32_100.14.09.html)

---

### Post by kapu on 2008-06-23
> **btermeli said:**
> I have MSI Megabook S260, it performs really good with Ubuntu, detected all hardware  automatically. But ur choice has Nvidia graphic card, mine  has Intel 915 (preinstalled on ubuntu 8.04).
For graphic card check the link;

[http://ubuntuforums.org/showthread.php?t=494041](http://ubuntuforums.org/showthread.php?t=494041)

Also Nvidia has Linux driver;

[http://www.nvidia.com/object/linux_display_ia32_100.14.09.html](http://www.nvidia.com/object/linux_display_ia32_100.14.09.html)

So, graphic will be OK. What about other HW?

---

### Post by dragonny on 2009-05-04
I have MSI EX700X and it runs very good under Ubuntu 8.04 (Hardy Heron).
I have one problem and that is web camera, it don't work.
But I found some drivers (which I didn't tested) on this page: [http://sourceforge.net/projects/m560x-driver/](http://sourceforge.net/projects/m560x-driver/)
Anyway notebook is great (you can't buy better for same amount of money).

---

### Post by tofiluk on 2009-05-04
i have an MSI Wind which dual boots windows xp and ubuntu. ubuntu works perfectly however, the same problem as above is that i can't use my webcam. anyway, maybe i can fix this problem soon. hehehehe...

---

### Post by dragonny on 2009-05-10
Download source from here: [http://m560x-driver.svn.sourceforge.net/viewvc/m560x-driver/](http://m560x-driver.svn.sourceforge.net/viewvc/m560x-driver/)

Than install recording to these instructions: [http://m560x-driver.wiki.sourceforge.net/install_m560x_driver](http://m560x-driver.wiki.sourceforge.net/install_m560x_driver)

I have installed that on Ubuntu Hardy Heron (8.04.2) and it works!!!

Mine installation (in short) gone like this:
-Install libv4l
-Install m5602

Runned in Ekiga and it works, although image is not very good (too dark, without possibility to modify settings), but I think in Interpid/Jaunty that will be much better.

---

