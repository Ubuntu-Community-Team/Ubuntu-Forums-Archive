---
title: "ATI Radeon screen distortion on 10.04 and 10.10"
date: 2010-10-20
forum: Hardware
---

### Post by clauseng on 2010-10-20
I have a Gateway LT3103 Netbook that I was running Ubuntu 9.10 great.  I first upgraded to 10.04 LTS and whenever I pulled up a web page with flash components it would completely distort the screen, so I re-installed 9.10.  I waited until 10.10 and installed a clean install with it and still have the same problem.  The video is ATI Radeon.  

I don't understand why 9.0 and 9.10 both worked fine, but a newer release would have such problems.  Is there any fix?

---

### Post by clauseng on 2010-10-24
I just downloaded the ATI linux display driver 10.10 from the following URL, then installed it and the display appears to be stable now with a variety of tests that I was previously able to get the display to distort with:

[http://www2.ati.com/drivers/linux/ati-driver-installer-10-10-x86.x86_64.run](http://www2.ati.com/drivers/linux/ati-driver-installer-10-10-x86.x86_64.run)

After download, to install this, go to the directory you downloaded it to, then:

  su sh ati-driver-installer-10-10-x86.x86_64.run

I found that trying to generate the distro specific package didn't work.  An error was produced and no package was generated.  I reran it and just selected the default install with the automatic options and it installed ok without errors.  I then rebooted my machine and the display has been stable since.

---

