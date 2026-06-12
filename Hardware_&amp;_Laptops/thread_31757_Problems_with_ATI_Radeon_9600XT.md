---
title: "Problems with ATI Radeon 9600XT"
date: 2005-05-04
forum: Hardware &amp; Laptops
---

### Post by Yotam2 on 2005-05-04
Hello,

I tried to install the ATI drivers on the default repositories, but it messed up my sound somewhy so I uninstalled it using synaptic (marked for complete removal), restored the former xorg.conf and restarted X successfully. Then I downloaded the latest RPM's from ATI (v. 6-8-0 _8.12.10_i386), used synaptic to get my kernel headers (linux 686 2.6.10-5), used alien to convert the RPM into .deb file and installed it using dpkg -i. Then I installed successfully the kernel module from /lib/modules/fglrx and used fglrxconfig to generate a new xorg.conf.

when I restarted X, I got only MESA accelleration. In /var/log/Xorg.0.log, I get:: 
(II) fglrx(0): DRIScreenInit done
(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.8.25
(II) fglrx(0):     Date: Jan 14 2005
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(WW) fglrx(0): Kernel Module version does *not* match driver.
(EE) fglrx(0): incompatible kernel module detected - HW accelerated OpenGL will not work

as you can see, this is the wrong version of the kernel module! How can I get rid of it for good and use my new 8.12.10 module? what should I check? I'm relatively new to linux.

P.S. according to the log, fglrx recognized my card as Radeon 9600 Pro (Chipset (RV 360 4152) and not as 9600XT (chipset RV300 4146). Is this related to my problem? What syntax should I use to fix this in xorg.conf?

TIA!

---

### Post by Yotam2 on 2005-05-04
Update: I tried changing the chipsets in xorg.conf, but to no avail. Is it a problem of my linux kernel headers (the official ones), only supporting the old version of fglrx?

---

### Post by alastair on 2005-05-04
I'm not sure I'd expect just converting an RPM to Deb to work like this. The RPM often has problems on a Redhat system itself!

Firstly, installing the created Deb file probably did a build of the driver for your kernel - did you see the build? There should be a build log somewhere.

The build might have either failed, had warnings/errors or installed wrong. There's usually a sample load at the end as well - did this work?

Before building - make sure you are NOT in X, have unloaded the fglrx module - and perhaps checked for or deleted any old fglrx module under /lib/modules.

I don't think the recognition of card type has anything to do with your problem.

I think you are brave to try this install though.

---

### Post by lappy512 on 2005-05-04
usually when i install my ATI drivers (9600AIW) it breaks my system, and i get a terminal.

---

### Post by Yotam2 on 2005-05-04
Thanks for answering!

The ati site, If I remember correctly, recommends converting the RPM to Deb in Debian.The build (make_install.sh, which I run _after_ installing the Deb according to the documentation) went fine and without errors or warnings, and the sample load was successful. The new fglrx driver informed me in the Xorg log that it recognizes hardware, and initializes 2D support, hence it works... The weird thing is that the kerel module is still the old one. Is there any way I can find out the version of a running kernel module, or the version of the fglrx.ko file in /lib/modules that activates it? Is it possible to manually replace it? Or is it something to do with the misteryous kernel headers?

Oh, and one more thing I don't understand yet: When using modprobe to load a kernel module, will it still be there the next time I boot? Does it remember my request? Is that the point of /lib/mosules?

---

### Post by Yotam2 on 2005-05-05
Apparently I wasn't looking hard enough. The installation of the new kernel module was indeed unsuccessful (it needed some missing .cmd file - others have reported that as well).
I uninstalled my downloaded fglrx, and re-installed the older version in ubuntu repositories. After changing some definitions in ESD configuration, my sound problems with it dissappeared. And now I have 3d and I am happy.

Thank you all for listening to my troubles!

---

