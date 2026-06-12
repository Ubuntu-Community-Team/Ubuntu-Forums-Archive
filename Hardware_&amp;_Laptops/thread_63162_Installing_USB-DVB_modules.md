---
title: "Installing USB-DVB modules"
date: 2005-09-07
forum: Hardware &amp; Laptops
---

### Post by igb on 2005-09-07
I am trying to get my Avermedia USB-T TV to work. It seems that I need to install the DVB-USB drivers. I have checked out the drivers via CVS and made sure I have the kernel source installed. However, when I run make I get the following error:

Makefile:13: /lib/modules/2.6.10-5-386/source/.config: No such file or directorymake: *** No rule to make target `/lib/modules/2.6.10-5-386/source/.config'.  Stop.

I don't have a source directory under 2.6.10-5-386. Clearly I am missing something, so what do I need to install?

Secondly, according to [http://www.wi-bw.tfh-wildau.de/~pboettch/home/index.php?site=dvb-usb-howto](http://www.wi-bw.tfh-wildau.de/~pboettch/home/index.php?site=dvb-usb-howto) 

it will only work with kernel 2.6.12. Has anyone tried with the default Ubuntu kernel? Is there a 2.6.12 kernel available for Ubuntu, or do I need to build one from kernel.org?

Thirdly, hs someone hacked [http://www.linuxtv.org/wiki/index.php/Main_Page](http://www.linuxtv.org/wiki/index.php/Main_Page)  as most of the pages now seem to be empty.

Ian.

---

