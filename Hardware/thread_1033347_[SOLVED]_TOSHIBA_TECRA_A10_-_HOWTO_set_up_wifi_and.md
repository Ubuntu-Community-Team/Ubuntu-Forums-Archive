---
title: "[SOLVED] TOSHIBA TECRA A10 - HOWTO set up wifi and audio"
date: 2009-01-07
forum: Hardware
---

### Post by gawan on 2009-01-07
Hi guys,
I bought new TOSHIBA TECRA A10 (Core2Duo P8400, 2+1GB RAM, 250G, 15.4"W, DVDRW WL BT, 3G) and I after installation UBUNTU 8.10 wifi and audio did not work. I found many of unusable texts so I resolved write this short howto.

**wifi**

For this wifi:
```
Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

```

is solution:

```

sudo update-rc.d -f linux-restricted-modules-common remove
wget http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2
tar xvf compat*.tar.bz2
cd compat*
sudo apt-get update && sudo apt-get install build-essential
make
sudo make install
sudo make unload
sudo make load

```

[http://madberry.org/2008/11/how-to-get-atheros-ar242x-to-work-on-810-intrepid-ibex/]("http://madberry.org/2008/11/how-to-get-atheros-ar242x-to-work-on-810-intrepid-ibex/")

may be exists simplest way but this is functional.

**Audio**

I was despereted because a found tons of unusable tips a howtos. e.g irgpool, noacpi, compiling new alsa driver, but nothing works on my book. So I found so simplest solution to add to end of file
/etc/modprobe.d/alsa-base 
this line:
```
options snd-hda-intel model=toshiba
```

May be this solution is good for all toshiba tecra A10 notebooks.

this page help me: [http://ubuntuforums.org/showpost.php?p=5131958]("http://ubuntuforums.org/showpost.php?p=5131958")

---

### Post by nigelcliffe on 2009-03-27
Many thanks for the above posting.  My Tecra A10 worked fine on Wireless, but no audio with Ubuntu 8.10.  Your solution is very clear and works.  

Note for others, follow the link through for details of how to open the editor as superuser.

---

### Post by bbdanilo on 2010-01-19
Hello!

I have the same problem of Gawan with sound card of toshiba tecra a10.
I tried the suggested steps...NO RESULTS.
Are there people with new and correct solution of my problem?

thanks.

---

