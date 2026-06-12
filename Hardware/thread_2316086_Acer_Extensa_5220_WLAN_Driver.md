---
title: "Acer Extensa 5220 WLAN Driver"
date: 2016-03-04
forum: Hardware
---

### Post by ibrahim16 on 2016-03-04
Hello all
First I'm truly glad that I'm now an Ubuntu user, it's really grate.

My problem is, in my Acer Extensa 5220 Laptop, I can not install my Broadcom 802.11g Network Adaptor driver, I'm sure that I'm missing something, so would you please walk me through it?

Thanks.

---

### Post by ibrahim16 on 2016-03-04
Update:
I'm using Ubuntu 15.10, OS Type 32-bit.

---

### Post by weatherman2 on 2016-03-04
You'll probably get better response by posting in the Networking & Wireless forum - you can request to have this thread moved there.  But your solution should be fairly easy if you find the exact Broadcom wireless card you have.  You can find it most likely by typing this command in a terminal:

```

sudo lshw -C network

```

and then search the forums for the name of your wireless card (maybe it's BCM4313) along with "ubuntu" - you'll find a solution.  You might want to be online with a wired network cable temporarily to make that work, though.

If you are new to Ubuntu, I highly recommend you stick to an LTS version like Ubuntu 14.04 LTS which will be supported until 2019.  Ubuntu 15.10 support lasts only nine months, then you must upgrade (but you can upgrade to the upcoming 16.04 LTS).  Also, if you are starting over, consider the 64-bit version of Ubuntu.  (I'm pretty sure the CPU in your laptop is 64-bit.)  Some software (like Google Chrome browser) is no longer supported in the 32-bit version of Ubuntu.

And if you have not upgraded the RAM to 2GB in your laptop, you should.  It's very cheap to do if you buy used RAM on eBay.  I have recently upgraded the RAM on very similar laptops - using two 1GB PC2-5300 DDR2 sticks of SO-DIMM RAM, less than $5 USD shipped on eBay within the US.  More RAM will make a big difference in basic performance.

---

