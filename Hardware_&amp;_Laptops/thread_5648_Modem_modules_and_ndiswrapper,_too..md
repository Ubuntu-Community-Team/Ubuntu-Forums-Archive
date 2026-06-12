---
title: "Modem modules and ndiswrapper, too."
date: 2004-11-20
forum: Hardware &amp; Laptops
---

### Post by az on 2004-11-20
Here are some modem modules I compiled using the stock Warty kernel headers.

Lucent linmodem driver:
[www.vif.com/users/mzajac/ltmodem-2.6.8.1-3-386_8.31a9_i386.deb](www.vif.com/users/mzajac/ltmodem-2.6.8.1-3-386_8.31a9_i386.deb)

Ndiswrapper 0.11 (My prism2_usb device needs this to work)
[www.vif.com/users/mzajac/ndiswrapper-modules_0.11-2.6.8.1-3-386_i386.deb](www.vif.com/users/mzajac/ndiswrapper-modules_0.11-2.6.8.1-3-386_i386.deb)
[www.vif.com/users/mzajac/ndiswrapper-utils_0.11_i386.deb](www.vif.com/users/mzajac/ndiswrapper-utils_0.11_i386.deb)

SL-Modem modules compiled from the source package in universe:
[www.vif.com/users/mzajac/sl-modem-modules-2.6.8.1-3-386_2.9.9-1_i386.deb](www.vif.com/users/mzajac/sl-modem-modules-2.6.8.1-3-386_2.9.9-1_i386.deb)
###EDIT###
MULTIVERSE, not universe.  You still will need the sl-modem-source package since sl-modem-daemon depends on it.  Try to download the two sl-modem packages (daemon and source).  
[http://archive.ubuntu.com/ubuntu/pool/multiverse/s/sl-modem/sl-modem-daemon_2.9.9-1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/multiverse/s/sl-modem/sl-modem-daemon_2.9.9-1_i386.deb)
[http://archive.ubuntu.com/ubuntu/pool/multiverse/s/sl-modem/sl-modem-source_2.9.9-1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/multiverse/s/sl-modem/sl-modem-source_2.9.9-1_i386.deb)

sudo dpkg -i sl-modem-deamon* sl-modem-s*
it will complain about dependancies - they are all found on your cd.  Get them with:
sudo apt-get -f install

By default, sl-modem-daemon  will try to use the GPL alsa driver for the intel chipset)  You may need to edit /etc/default/sl-modem-daemon to specify the device if 'auto' fails.
SLMODEMD_DEVICE=hw:0   #(or hw:1depends on your soundcard, I guess)

If it still don't work, download and install the modules (or make them youself...)  

Then reconfigure sl-modem-daemon to use the slarm modules instead of the snd_intel8x0m module...

sudo dpkg -i sl-modem-modules*
sudo dpkg-reconfigure sl-modem-daemon

Sorry for the confusion.
If these do funny things to your system, It's not my fault...
I have described how to build these in earlier posts...

---

### Post by az on 2004-11-27
Some people may have had problems due to dependancies.  I edited the above post.
Has this helped anyone?
I will soon make a how-to...

---

### Post by poptones on 2005-01-24
I have tried this package and another, neither work. Have you made any progress on this? I'm trying to wean a friend from the suckalicious mandrake, not having a modem means that ain't happening.

The "ltmodem...deb" package doesn't even install the ltmodem.ko in my system. Running the scan program tells me this modem is supported, but the deb packages don't put the modules where they belong. Tried copying them to lib/modules/, they still don't seem to work.

---

### Post by az on 2005-01-24
The problem lies with somewhere with the ltmodem script being able to hande kernel-headers (and debian kernel versions named their way) but not being able to handle ubuntu linux-headers version numbers.  The problem may also be a bug in kernel-package.  Marv from linmodems.org posted a cryptic note about this recently on the mailing list.

The kernel from Warty also has been updated, so you would need to make a module for warty's old insecure kernel and one so that you would be able to get onto the net and download the new one.

You need to install a backported version (from Hoary) of kernel-package and try to compile the module with that.  You should compile it against the old kernel and the new kernel.  Module packages made with the backported hoary kernel-package should install fine on an out-of-the-box Warty.

I cannot do any of this at work and I have two small kids - my time spent with any computer that has Ubuntu on it conflicts with their needs.  This has been on my list of to do things....

Please try to do the above and let me know what you get.

Lucent's policy of providing proprietary drivers for linux is better than most other modem manufacturers, but they still do not provide a totally free (open, libre)driver.  This bugs me and has probably led to this falling from the top of my list.  Not to mention that I no longer own one of these modems.

 
Thanks!
Please do not hesitate to ask any other questions.  I had posted detailed instructions on how I had built the driver (It did work in debian Sarge) but they got shipped into the archives or something.

---

