---
title: "help how do I get this firmware into the linux kernel ?"
date: 2010-12-09
forum: Hardware
---

### Post by blokeinlondon on 2010-12-09
help how do I get this firmware into the linux kernel ?

Here is the problem in launchpad
[https://bugs.launchpad.net/ubuntu/+source/linuxtv-dvb-apps/+bug/618276](https://bugs.launchpad.net/ubuntu/+source/linuxtv-dvb-apps/+bug/618276)

here is where I think the firmware needs to be in the kernel
[https://github.com/mirrors/linux-2.6/tree/master/firmware/ttusb-budget](https://github.com/mirrors/linux-2.6/tree/master/firmware/ttusb-budget)

workaround for this error is to place file dvb-fe-tda10045.fw into
/lib/firmware

The problem is I don't know how to do this ?

normally my digg submissions get buried

my reddit submissions get supressed

ubuntu forums get closed

and my ubuntu launchpad bugs just expire .....

---

### Post by coffeecat on 2010-12-09
You don't have to put anything into the kernel. You simply copy the file into /lib/firmware/. Do you have the dvb-fe-tda10045.fw file already? If so, from the terminal:

```
sudo cp /path/to/dvb-fe-tda10045.fw /lib/firmware/
```That means that if the file is on your desktop, then you:

```
sudo cp ~/Desktop/dvb-fe-tda10045.fw /lib/firmware/
```But there might be an even easier way. If you use Synaptic or Ubuntu Software Centre to install the package linux-firmware-nonfree, the firmware dvb-fe-tda10046.fw (in Maverick/10.10) gets installed to /lib/firmware. This is a later version of the same firmware so it should do as well or perhaps even better.

I don't know which version of the firmware gets installed if you are running Lucid/10.04 but try it and see.

---

### Post by blokeinlondon on 2010-12-09
Thanks that might explain why it used to work !

---

### Post by coffeecat on 2010-12-09
> **blokeinlondon said:**
> Thanks that might explain why it used to work !

Yes. Probably in Jaunty, I guess. I notice from your Launchpad thread that your card has a Philips chipset. I have a dvb card with a (different) Philips chipset which worked just fine in Jaunty but failed to work in a default install of Karmic. That's when I discovered that the free and nonfree firmware had been separated into two packages for Karmic onwards. I'm surprised that no one told you of this in Launchpad. It's a licensing issue rather than a bug.

---

