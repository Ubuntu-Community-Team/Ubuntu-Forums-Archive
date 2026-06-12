---
title: "Linmodem for Motorola SM56?"
date: 2004-12-10
forum: Hardware &amp; Laptops
---

### Post by jchristian on 2004-12-10
Hi Folks!

I'm a total newbie to Linux, so forgive me in advance if my phraseology is wrong , or if I say something totally daft...

I have requested a copy of "Warty", with the intention of replacing Winbloze on my home PC. Linux seems much more versatile, and I'm just tired of supporting Bill G. and the Evil Empire....In the meantime, I'm trying to educate myself as much as possible to make the transition (hopefully) painless.

Here is my question: In some of the various Linux forums, I've come across dicussions of  winmodem/linmodem. I gather that a linmodem is simply a driver that makes a particular (win)modem's chipset function under a particular kernel and/or distribution. (is this correct?)
My existing computer has installed a Motorola SM56 PCI modem. Motorola offers drivers for Redhat 7.1 and SUSE (var releases) but has announced that they no longer support new Linux distributions, and have no intention of doing so in the future.

Does any one know of a linmodem download for my modem, or of a work-around that might help? Or should I start shopping for another modem?

Thanks in advance for any advice,
jchristian

---

### Post by az on 2004-12-10
Start shopping for a new modem.

[http://search.ebay.com/smartlink-modem_W0QQsojsZ1QQfromZR40](http://search.ebay.com/smartlink-modem_W0QQsojsZ1QQfromZR40)
[http://search.ebay.com/lucent-modem_W0QQfromZR40QQsojsZ1](http://search.ebay.com/lucent-modem_W0QQfromZR40QQsojsZ1)

---

### Post by jchristian on 2004-12-11
That's what I figured.....Do you have any specific recommendations as to brand/model? I noticed you linked to Smartlink and Lucent. Are those fairly equal in terms of stability, software, ease of installation, etc?

Thanks for taking the time to respond!

---

### Post by poptones on 2004-12-11
I setup a friend with linux and had to replace her lucent modem because the only drivers I could find sucked. I bought a motorola sm56 and isntalled it, it worked just fine with the drivers from the motorola website.

That's with mandrake. Haven't yet tried it with ubuntu; likely you'll need to unpack the rpm and move the filles where they belong manually. Add "sm56" to the modules.conf file, type "modprobe sm56" on the command line and try it.

---

### Post by jchristian on 2004-12-11
Thanks for the advice poptones. I'll give that a shot, see what happens.
Do you know of a hardware compatibility list for Linux? While I'm waiting for my copy of Warty, I might as well make sure the rest of my hardware will work...
Thanks!

---

### Post by az on 2004-12-11
That wont work with ubuntu.  I am not sure that the drivers provided by Motorola are for a 2.6 kernel.  Anyway, they do not support linux if they just make one driver for one linux distribution.  As as as I Know, the driver is fairly unstable in Mandrake anyway.

Smartlink have nice linux drivers.  They are proprietary, of course.  Lucent also have great drivers, the script for making debian packages for the 2.6 kernel version is currently broken and will be fixed soon.  You can always install the compiles modules by hand...

You can also just get a hardware modem...

---

