---
title: "Dell Latitude D600"
date: 2005-02-05
forum: Hardware &amp; Laptops
---

### Post by Mumra on 2005-02-05
I've been fighting for a while to get Ubuntu working on the Dell Latitude D600 - there's a lot of help in these forums, which I'm eternally grateful for. I've pulled together my efforts into a neat little article which will get you up and running with wireless, 3D, XV and so on.

I hope it's useful for someone out there!

[http://www.shahidhussain.com/wordpress/index.php?p=30](http://www.shahidhussain.com/wordpress/index.php?p=30)

---

### Post by kdavison007 on 2005-02-06
Nice.  I think at work I'll be getting the new D610 with the Sonoma chip.  Hopefully, it will be a similar installed, but I'm guessing PCI-x might give me some trouble.

---

### Post by bobthomp on 2005-04-29
As a Linux user with a Dell D610 ... except that I'm using the Fedora Core 3 distro, not Ubuntu, sorry!  Perhaps this will be helpful for you.  Or perhaps someone else asking Mr. Google for help.  :-)

Because Dell likes to mix-and-match hardware, even in the Latitude line, here's my specifics:

Pentium M 760 (2.0Ghz), SXGA Display (the new Sonoma chipset)
Radeon Mobility X300 Video 
80GB 5400 RPM Hard drive
512 MB DDR2 RAM
Intel Pro Wireless 2200 
8x DVD+/-RW optical drive
Intel PRO/Wireless 2200 WLAN (802.11b/g) miniPCI

Graphics-wise, I don't care much about 3D.  The FC3 installer worked automagically created a /etc/X11/xorg.conf file that does 1400x1050 with 24 bit color.  "glxgears" claims about 650 frames/sec.  The only change I made in the xorg.conf file was to comment out the 'Load "dri"' line from the "Module" section.

Downloading and installing the ipw2200 drivers from [http://2200.sourceforge.net/](http://2200.sourceforge.net/) was straightforward.

Suspend to RAM (S3) has been impossible.  I've followed many Dell D600 instructions for doing it, but none of them work (despite using 2.6.9, 2.6.10, and 2.6.11 kernels, with and without the "late s3" patch that's floating around): suspend to RAM is fine, but the resume / wakeup gives a hard drive hang & timeout.  I finally gave up and patched a 2.6.9 kernel to use the Software Suspend 2: [http://www.suspend2.net/](http://www.suspend2.net/).  The default /etc/hibernate/hibernate.conf file works.

If anyone with a D610 manages to get S3 suspend to RAM *and* a successful resume to work, PLEASEPLEASEPLEASE share how you did it with the rest of the world.

While compiling various kernels, I found that some didn't permit the eraser pointer to work.  Or the eraser pointer would work but the mouse buttons underneath the spacebar didn't.  I think my kernel ".config" file is one I borrowed from a Fedora Core 2.6.9 kernel source RPM, but I don't remember.  If anyone encounters a problem with the eraser pointer, contact me, and I'll try to figure out the magic.

---

