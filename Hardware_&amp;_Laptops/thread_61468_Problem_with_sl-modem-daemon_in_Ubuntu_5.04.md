---
title: "Problem with sl-modem-daemon in Ubuntu 5.04"
date: 2005-08-31
forum: Hardware &amp; Laptops
---

### Post by Renan Birck on 2005-08-31
Hello,

I installed Ubuntu 5.04 - received my Ubuntu CD's today. Great work! - successfully, and followed the instructions at [http://ubuntuguide.org/#installsmartlinkdriver](http://ubuntuguide.org/#installsmartlinkdriver) to install LG winmodem (works with SmartLink driver in other Linux distros).

But when I try to use it, there is no connection: the modem dials but hangs up after a while. I use the winmodem successfully in Slackware Linux.

I saw that the package' version is 2.9.9, while the driver that works for me is version 2.9.10.

Anybody has links for a 2.9.10 .deb package, or updated modules? I can't compile on my own because I'm stuck in a Catch 22: I need to download the kernel source and compilers, but I don't have a network connection.

Thanks!

---

### Post by az on 2005-08-31
You do not need the full source.  All you need are the kernel headers which are found in the linux-headers-2.6.10-5-386 package on your cd.  Install it along with build-essential and you are good to go.  

Any sl-modem-drivers (source or binary) after 2.9.9a are under a different licence and cannot be distributed legally, unless you own smartlink hardware.  This driver happens to work for a number of other brands of modems.

---

