---
title: "Only 800x600 on Thinkpad X31 after 8.10 upgrade"
date: 2008-11-07
forum: Hardware
---

### Post by 67north on 2008-11-07
Hi,
  after upgrading to 8.10 I can only get X working with the "vesa" driver, and I cannot get 1024x768 resolution, only 800x600. 
The "ati" driver gives me errors. 
I followed the instructions on [http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide) to install the "fglrx" drivers, but that also give me errors. 
Enclosed are log files. 
This is a Thinkpad X31, and X worked well before the upgrade.

---

### Post by Yellow Pasque on 2008-11-07
fglrx does not support your card (it's too old). Make sure you uninstall all the fglrx packages (you can leave fglrx-modaliases if you wish). You'll have to get the ati/radeon driver to work.

---

### Post by 67north on 2008-11-07
Too old?  I guess that is a problem with Thinkpads, they last too long :)

I removed all fglrx packages, did a
$ sudo dpkg-reconfigure xserver-xorg
and inserted 
Driver "ati"
in xorg.conf

Now 1024x768 is working. 
Thanks!

---

