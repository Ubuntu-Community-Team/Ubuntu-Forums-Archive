---
title: "Problem installing new ATI driver"
date: 2009-08-29
forum: Hardware
---

### Post by dbcoolio on 2009-08-29
I saw this post: [http://www.ubuntugeek.com/ati-linux-video-driver-9-8-now-supports-ubuntu-9-04-jaunty.html](http://www.ubuntugeek.com/ati-linux-video-driver-9-8-now-supports-ubuntu-9-04-jaunty.html) 
and since I have an ATI radeon card, I thought I'd try the new driver.

After mucking around with it, I don't think it supports my hardware. I have a: VGA compatible controller: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)
(from lspci)

Part of the problem is that I ran the driver install script with the default parameters the first time, so it did it's redhat thing and wrote directly to the kernel without any sort of dpkg involvement.  And I can't find any way to reverse it.

After that didn't work I tried the instructions from here: [http://webupd8.blogspot.com/2009/08/amd-catalyst-98-released-how-to-upgrade.html](http://webupd8.blogspot.com/2009/08/amd-catalyst-98-released-how-to-upgrade.html)

and that seemed like the right way to do it, but it didn't work.  Then I tried doing it from ENVYNG, but it said my hardware wasn't compatible.

So I tried removing all the packages in synaptic, and reinstalling them (anything having to do with the kernel or xorg) and I have also tried dpkg-reconfigure xserver-xorg and neither of them seem to have gotten me back on the open source driver I was using before all this mess (everything worked with it - including compiz and RandR - except for my s-video out port)

So what can I do to get back on the open source driver?

thanks

---

### Post by dbcoolio on 2009-08-29
I also tried this out: [http://www.h-online.com/open/Updated-graphics-drivers-for-Ubuntu-9-04--/news/113261](http://www.h-online.com/open/Updated-graphics-drivers-for-Ubuntu-9-04--/news/113261)

---

### Post by dbcoolio on 2009-08-29
I got it working!

I followed these instructions: [https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver)

as well as rm -rf /etc/ati

and reinstalled compiz

---

