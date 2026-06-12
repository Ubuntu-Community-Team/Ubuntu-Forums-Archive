---
title: "Drivers for Intel HD Graphics 3000"
date: 2014-03-10
forum: Hardware
---

### Post by jaspreet on 2014-03-10
A very basic question regarding Graphics hardware in my Acer laptop. It has an Intel chipset as shown below and working great without installing any extra graphic drivers. Would it still make sense to install Intel's opensource drivers using intel-linux-graphics-installer? What kind of leverage would it give me?

root@jaspreet:~# lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
root@jaspreet:~#

---

### Post by sudodus on 2014-03-10
I'm running similar Intel graphics hardware with the built-in driver and have not bothered to install  Intel's opensource driver. It is different with nvidia and AMD/ATI/Radeon, where there is really a big difference in performance.

But I have to admit, that I don't know much about Intels own drivers and 3D capability. Let us wait for more replies.

---

### Post by Yellow Pasque on 2014-03-10
> **jaspreet said:**
> Would it still make sense to install Intel's opensource drivers using intel-linux-graphics-installer?

No, this is an "if it ain't broke, don't fix it" situation. I've seen too many people bork their graphics drivers trying to install drivers directly from intel (or AMD or Nvidia) website.

If you want to play with the latest drivers and see if it gives you a couple extra FPS, see the xorg-edgers PPA: [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

---

### Post by oldfred on 2014-03-10
You may have a good driver.

Intel has been making many improvements to its open source driver, but it mostly is for Haswell and Broadwell or the newest versions. And the updates are not just the video driver but the kernel & lots of support software, so you need the full system. 
If running 13.10 or 12.04.4 you probably have the most current version for your 2nd gen and only if some of the updates to the newest video chips also help the older one's will their be any improvement.

I do not know if any comments in this refer to older versions also:
 Haswell improvements thru 2013
[http://www.phoronix.com/scan.php?page=article&item=intel_2013haswell_end&num=1](http://www.phoronix.com/scan.php?page=article&item=intel_2013haswell_end&num=1)

---

