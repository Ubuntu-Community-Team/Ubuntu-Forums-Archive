---
title: "Can I run Ubuntu on my old comp?"
date: 2013-05-31
forum: Hardware
---

### Post by metalbig on 2013-05-31
Hello!
I am totally new to linux. I would like to run Ubuntu, but I am not sure that my old comp is supported.
Generally my concern is about if there are linux drivers for my hardware.


MainBoard: MSI 915PL Neo - [http://www.msi.com/product/mb/915PL-Neo.html](http://www.msi.com/product/mb/915PL-Neo.html)
RAM: 768 MB (soon will be 1 GB)
CPU: Intel Celeron D341 (2.93 GHz) - [http://ark.intel.com/products/27122/](http://ark.intel.com/products/27122/)
Video: Asus Extreme AX550 (128MB) - [http://www.asus.com/Graphics_Cards/Extreme_AX550TD128M/](http://www.asus.com/Graphics_Cards/Extreme_AX550TD128M/)


Can you please help me with this: is my hardware supported?

---

### Post by Autodave on 2013-05-31
I don't see any reason why it wouldn't.  With any flavor of Linux, you can boot and "test-drive Linux.  Note: it will be MUCH slower running from a USB stick or from a DVD, but that will at least tell you if your hardware is supported.  If everything looks OK, you can then proceed to install it.  

Ubuntu is very fancy and requires a lot more RAM than doed Xubuntu or Lubuntu.  My suggestion would be to try Xubuntu first: either 32 bit or 64: whichever your machine is.  After install, then we can look at installing any additional drivers you may need to make video better, wi-fi work, etc.

---

### Post by ahallubuntu on 2013-05-31
~

---

### Post by sanderj on 2013-05-31
> **metalbig said:**
> Hello!
I am totally new to linux. I would like to run Ubuntu, but I am not sure that my old comp is supported.
Generally my concern is about if there are linux drivers for my hardware.


MainBoard: MSI 915PL Neo - [http://www.msi.com/product/mb/915PL-Neo.html](http://www.msi.com/product/mb/915PL-Neo.html)
CPU: Intel Celeron D341 (2.93 GHz) - [http://ark.intel.com/products/27122/](http://ark.intel.com/products/27122/)
Video: Asus Extreme AX550 (128MB) - [http://www.asus.com/Graphics_Cards/Extreme_AX550TD128M/](http://www.asus.com/Graphics_Cards/Extreme_AX550TD128M/)


Can you please help me with this: is my hardware supported?

Your CPU has PAE, which is required for current Ubuntu versions, so that's good.

How much RAM is installed?

---

### Post by metalbig on 2013-05-31
Now it is 768 MB (soon will be 1 GB) - I hope it can work with this RAM that I have.

I've checked on MSI and ASUS sites for linux drivers, but there are not any. This is my biggest concern - if Ubuntu supports them?

---

### Post by ahallubuntu on 2013-05-31
~

---

### Post by sanderj on 2013-05-31
> **metalbig said:**
> Now it is 768 MB (soon will be 1 GB) - I hope it can work with this RAM that I have.

I've checked on MSI and ASUS sites for linux drivers, but there are not any. This is my biggest concern - if Ubuntu supports them?

769 MB is a bit low for the current Ubuntu. Maybe you should consider Xubuntu or Lubuntu.

No worries about your motherboard ... it will work.

---

### Post by metalbig on 2013-05-31
Well I have already made one test run with Ubuntu Live DVD x86 - it started. Access to files on HDD - OK. Firefox is working - network is running.
But because for video card it was shown "not known" - that's why I was afraid that my hardware is not supported.

BTW sorry for the stupid question (:)) but what are Xubuntu and Lubuntu??? Probably some lighter versions of Ubuntu? 
If yes, then are these versions capable to support same software which Ununtu can support?

---

### Post by Mark Phelps on 2013-05-31
According to the video link, your video chipset is an OLD X300 -- for which AMD has not written drivers for a LONG time!  While it's possible that the default Radeon drivers might work, if they don't, you'll be basically Out of Luck, because there are no other drivers available for this chipset.

---

### Post by Yellow Pasque on 2013-05-31
> But because for video card it was shown "not known" - that's why I was afraid that my hardware is not supported.
That's a cosmetic error. [https://bugs.launchpad.net/ubuntu/+bug/946620](https://bugs.launchpad.net/ubuntu/+bug/946620)
The video card is supported by the default radeon driver, so no need to mess with drivers.

---

### Post by Yellow Pasque on 2013-05-31
>  what are Xubuntu and Lubuntu??? Probably some lighter versions of Ubuntu?
If yes, then are these versions capable to support same software which Ununtu can support? 
All the Ubuntu derivatives use the same repository, so you can install whatever you want. I would persoanlly use Xubuntu (32-bit) on a machine like that, but I'm not a big fan of the Unity desktop...

---

