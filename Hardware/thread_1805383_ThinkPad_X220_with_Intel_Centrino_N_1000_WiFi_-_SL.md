---
title: "ThinkPad X220 with Intel Centrino N 1000 WiFi - SLOW"
date: 2011-07-15
forum: Hardware
---

### Post by steevven1 on 2011-07-15
I just did a clean install of Xubuntu 11.04 on a ThinkPad X220 with an Intel Centrino Wireless-N 1000 WiFi card, and my download speeds never exceed 50 kB/s on a great connection, where my other laptops get ~1 MB/s down.

Any ideas? This is absolutely killing me. I just spent over $1000 on this laptop!

---

### Post by steevven1 on 2011-07-15
FIXED!

Apparently, this WiFi card screws up on Linux when "N" network support is enabled. Disable N network support, and it works beautifully. To do so, do the following:

sudo vi /etc/modprobe.d/iwlagn.conf

Add the following line to this file (which was probably empty before):

options iwlagn 11n_disable50=1 11n_disable=1

Be happy.

---

### Post by sawtoothX on 2012-01-16
In my case (x220 i5) the fix breaks wireless completely. The interface disappears.

Is there a better set of drivers?

By the way on Ubuntu 11.10:

$ uname -a
Linux sawtooth-x220l 3.0.0-14-generic-pae #23-Ubuntu SMP Mon Nov 21 22:07:10 UTC 2011 i686 i686 i386 GNU/Linux

---

### Post by rmiloh on 2012-01-29
The Intel Centrino N 1000 didn't work for me.  I disabled N, installed wicd, and got reasonable use out of it for only short periods. 

Because of the lenovo bios whitelist for approved wireless mini-pcie cards, you can't just upgrade the hardware to something that works

  
Check out the thinkwiki wiki page about it the wireless-n 1000
[http://www.thinkwiki.org/wiki/Intel_Centrino_Wireless-N_1000](http://www.thinkwiki.org/wiki/Intel_Centrino_Wireless-N_1000)


If there is no software fix on the horizon and you must get it working, then try using a lenovo approved Intel centrino N-6205 from ebay or a reseller you trust that guarentees the device will be 'whitelisted' in the bios
 [http://www.thinkwiki.org/wiki/Intel_Centrino_Advanced-N_6205](http://www.thinkwiki.org/wiki/Intel_Centrino_Advanced-N_6205)

---

