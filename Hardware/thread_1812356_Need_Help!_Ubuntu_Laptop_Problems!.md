---
title: "Need Help! Ubuntu Laptop Problems!"
date: 2011-07-26
forum: Hardware
---

### Post by Joutei on 2011-07-26
Hey guys.

I have a Hp Dv6-3041tx.
Specs:

Intel i7 1.6ghz
Amd Radeon hd 5650
500gb hard drive 
8gb ram

I have installed and runned both ubuntu 11.04 and 10.4 32 and 64 bit.

They both run really bad.
Very unstable, freezes lock ups ,etc.

64bit is preferable so I can use the whole 8gb of ram.

I've used ubuntu on my desktop and it was wonderful.
Doesn't seem to like my laptop much.

Please help :( 

Also i have read the 3.0 linux kernal was realeased, how would install this.
Thanks.

:guitar:

---

### Post by mastablasta on 2011-07-26
did you install the ATI drivers? if you did, did you then try to install newer version?

---

### Post by Joutei on 2011-07-26
can that be the problem of freezes and laggs etc ?

---

### Post by realzippy on 2011-07-26
+1 for ATI/AMD drivers.

> **Joutei said:**
> 

Also i have read the 3.0 linux kernal was realeased, how would install this.
Thanks.

:guitar:

32 bit:
Install in that order:
[1.]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.0-oneiric/linux-headers-3.0.0-0300_3.0.0-0300.201107220917_all.deb")
[2.]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.0-oneiric/linux-headers-3.0.0-0300-generic_3.0.0-0300.201107220917_i386.deb")
[3.]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.0-oneiric/linux-image-3.0.0-0300-generic_3.0.0-0300.201107220917_i386.deb")

64bit:
[1.]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.0-oneiric/linux-headers-3.0.0-0300_3.0.0-0300.201107220917_all.deb")
[2.]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.0-oneiric/linux-headers-3.0.0-0300-generic_3.0.0-0300.201107220917_amd64.deb")
[3.]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.0-oneiric/linux-image-3.0.0-0300-generic_3.0.0-0300.201107220917_amd64.deb")

...note,that probably won't fix your graphics.

---

### Post by Joutei on 2011-07-26
so ati has drivers for ubuntu linux ? via their website?
cheers

---

### Post by Joutei on 2011-07-26
Hmm I'm unsure if the ati graphics driver is the problem , what are some other common issues causing freezes and lags in ubuntu

---

### Post by realzippy on 2011-07-26
Go to

System-Administration-Hardware(Additional)Drivers

If there is an ATI/AMD driver offered,install it.
Then you will see if this solves your issues.

---

### Post by Joutei on 2011-07-27
Will do. Anyone having simillar issues with 11.04 64bit ?

---

