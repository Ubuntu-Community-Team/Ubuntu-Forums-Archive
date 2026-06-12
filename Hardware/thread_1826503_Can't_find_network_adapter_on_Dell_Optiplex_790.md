---
title: "Can't find network adapter on Dell Optiplex 790"
date: 2011-08-16
forum: Hardware
---

### Post by avoncampe on 2011-08-16
I'd like to use the LTS release (so 10.04 at the moment), but when I install it on a new Dell Optiplex 790 it appears it doesn't include the right driver for the on-board Ethernet adapter.  I've been able to get the network going using a USB adapter, and I've already done the apt-get update/upgrade to install the latest updates and rebooted, but it still can't find the on-board network adapter.  Is there a way to get the latest drivers using the LTS release stream?

Alfred

---

### Post by Mahelita on 2011-08-17
Same here!

---

### Post by graham_midi on 2011-08-22
In the spirit of good Karma I think I have just solved this by following the advice on this link:

[http://giantdorks.org/alain/fix-for-non-working-wired-ethernet-on-dell-latitude-e6520-with-intel-82579-based-adapter-running-ubuntu-10-04-lts-lucid/](http://giantdorks.org/alain/fix-for-non-working-wired-ethernet-on-dell-latitude-e6520-with-intel-82579-based-adapter-running-ubuntu-10-04-lts-lucid/)

I by no means know what I am doing, but it worked. (I just switched the driver version number to the more current ones listed rather than the one's Alan used.)

Hope this helps

---

