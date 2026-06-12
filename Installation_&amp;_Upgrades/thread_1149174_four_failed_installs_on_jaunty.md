---
title: "four failed installs on jaunty"
date: 2009-05-05
forum: Installation &amp; Upgrades
---

### Post by quotaholic on 2009-05-05
On my four fails each one was different. I opted for ext4 as my root partition each time. I ran ubuntu 9.04 beta with no issues on  this board so I thought it would be safe. 

On install one I used the AMD64 release as I have an athlon based system. Corrupted graphics at the end o the install. I use an embedded x1250 and I opted for amd graphics.

On install two I grabbed the i386 version. This time it picked up a usb wireless device where as in amd64 did not. In the middle if the install the installer popped back out to step number one and acted just as if the live cd just had booted. Nothing installed.

Install three was in i386 again and I went through everything ok but when that wireless adapter gets recognized it shuts down other  portions of usb. My rf keyboard and mouse stopped working. Adide form that the myth tv setup screen had no text on it. I saw a rectangular box but no text. 

Install four. Same exact as install three. Only this time I tried to push through myth setup screen that had no text, again. Well that looked like it was going to work as the disc spun up. Then I got a crashed application notice and a black screen. 

I burned the disc on the slowest setting I had. I always let roxio verify an iso and this was no different. This exact hardware was just supporting a ubuntu i386 open source graphics based beta. Does anyone have any suggestions that I can check?  

quotaholic

---

### Post by Mark Phelps on 2009-05-05
First off, your ATI graphics won't work with the ATI driver (fglrx) anymore because support has been dropped.  Catalyst 9.3 is the last driver to support your chipset and it won't work on Ubuntu 9.04.  So, you'll have to use the open source driver.

Second, I had lots of problems with the LiveCD installer and resorted to using the Alternate CD.  Not as spiffy an installer, but it worked.

Good Luck

---

