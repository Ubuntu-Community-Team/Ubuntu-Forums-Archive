---
title: "Intel 536ep Modem working on Ubuntu 8.04 LTS (hardy)"
date: 2008-05-03
forum: Hardware
---

### Post by mssaleh5 on 2008-05-03
Hello, everyone.

I've found a recent Philippe Vouters' driver for intel 536ep modem on his website. I managed to compile and install the driver with a little change in the installation script. I have Ubuntu 8.04 LTS with 2.6.24 kernel, and I'd expect it to work on any similar configuration.

Simply download the attached archive, use a ROOT terminal and follow installation instructions.
Of course, you'll need the kernel headers installed and possibly some other development packages.

Good luck everyone!
:)

---

### Post by bctechnzl on 2008-05-06
Nice to find this recent post.  I've a machine we recently upgraded to dapper, previously being breezy and had a working 536ep setup. Can't seem to get the modem working nor will the driver compile.  I have the same modem working nicely under feisty in another machine, so am slightly stuck at the moment: Do I continue and upgrade this server to hardy simply to get the modem (for a fax server) to work?

My  question is:  Why are you using the 2.76 v driver and not the 4.71?
I'll try to attached the 4.71 driver I downloaded from Intels site with the possibility that you might like to try it. Can't quote the link, but it is on the Intel site if you prefer.

I don't know the differences, but will need to build another machine to test the scenario out with hardy if I can't figure another way.
Thanks again for your post, you've at least given me hope...

---

### Post by mugi on 2008-05-07
intel-536EP-2.56.76.0.zip  doesn't work. :-(

---

### Post by mssaleh5 on 2008-05-13
Hello.
Just in case google or something has directed you to this page. You may want to check this thread instead.
[http://ubuntuforums.org/showthread.php?t=471503](http://ubuntuforums.org/showthread.php?t=471503)
[http://ubuntuforums.org/showthread.php?t=471503]("http://ubuntuforums.org/showthread.php?t=471503")
It has a pre-complied .deb package and it is more convenient than my tweaked script.
Thank you.

---

