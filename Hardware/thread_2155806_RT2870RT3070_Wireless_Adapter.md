---
title: "RT2870/RT3070 Wireless Adapter"
date: 2013-06-19
forum: Hardware
---

### Post by Incarnadine on 2013-06-19
Does anyone know how to get the RT2870/RT3070 Wireless Adapter working for Ubuntu?

I tried looking for a driver at the Ralink website, but no luck.

---

### Post by Juvencio on 2013-06-19
Hi Incarnadine

I have drivers that worked for my RT5360 on 12.04 64bit. But after a couple of months it stopped, not sure what I did.

try this see if it works
[http://askubuntu.com/questions/310261/ralink-rt5360-wireless-not-working]("http://askubuntu.com/questions/310261/ralink-rt5360-wireless-not-working")


this is for the drivers that worked on 12.04
[http://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.9-rc4/compat-drivers-3.9-rc4-2-su.tar.bz2]("http://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.9-rc4/compat-drivers-3.9-rc4-2-su.tar.bz2")

Code:

sudo apt-get install linux-headers-generic build-essential

cd to folder

Code:

sudo su
./scripts/driver-select rt2x00
make
make install
exit

When there is an upgrade to the kernel you will need to recompile this driver:

Code:

sudo su
./scripts/driver-select restore
./scripts/driver-select rt2x00
make clean
make
make install
exit

I cant remember where I fount this, but thanks to the community I did find it.

---

