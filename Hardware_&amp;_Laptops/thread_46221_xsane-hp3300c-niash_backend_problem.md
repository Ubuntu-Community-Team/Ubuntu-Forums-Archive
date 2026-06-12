---
title: "xsane-hp3300c-niash backend problem"
date: 2005-07-03
forum: Hardware &amp; Laptops
---

### Post by jchristian on 2005-07-03
Here's an odd problem:

  I just installed a hp scanjet 3300c, using the niash backend from the sane-extra package. After the usual diddling with permissions, commenting out stuff in /sane.d/dll.conf, etc, my scanner is recognized by libusb,sane-find-scanner, scanimage, and xsane.

But...
  When I try to actually scan an image, the scanner makes loud clicking noises and Ubuntu crashes. ( processer maxed out, in other words) The only way to recover is to unplug the scanner and reboot Ubuntu. Sane-troubleshoot finds no problems, until it tries a test scan. Same thing happens. The troubleshoot log doesn't show anything until I unplug the scanner, at which point is says "failed". (no s--t, sherlock)

  The niash backend homepage mentions " if improperly configured, scanner will jam at top of bed and make loud clicking noises, unplug immediatly or damage to scanner will occur..", but they don't offer any solution or advice

  As far as I know, the only thing I configured was the scanner group permissions, and uncommented niash in dll.conf., while commenting out everything else.

 Is there another .conf file somewhere I'm missing? Frankly I'm confused. Any advice or insight would be greatly appreciated.

Thanks

---

### Post by SpEcIeS on 2005-07-03
I have been using a HP 3300c ScanJet for some time now with linux. There has been some improvements recently, and I believe that I have install deb packages outside of the Ubuntu 5.04.

When installing these packages, including xsane, I did not have to "diddle" around to get it working, however the scanner does, periodically, make loud clicking noises. I do not worry and just hope that it does not blow up.  ;-) So far so good.

In the past I have using sane to use this scanner while using SuSE 8.1, 9.2, debian 3.1, and now Ubuntu 5.04. As far as my system, and experience, goes; there should not be a problem.

Perhaps downloading the deb packages from the [Sane HomePage](http://www.sane-project.org/source.html) may help, good luck. :)

---

### Post by jchristian on 2005-07-05
Thanks for the advice!

The links to the deb packages were 404, but I installed the newest sane,xsane, and sane-backends from source, and now it seems to be working fine. The changelog for backends mentioned an bug-fix for the niash backend, so that might have been the cause of my original problem. The only caveat is that I have to remember to set "scanner settings" on the xsane frontend every time I scan, or it doesn't work......

If anyone else tries this here's a couple of tips:

You _must_ remove every trace of the original sane installation. I did "apt-get remove", and it left /usr/lib/libsane.so. and another few fragments that screwed up the first new installation.

Src installs to a different path than the distro sane, /usr/local/lib, instead of /usr/lib, so you have to edit /etc/ldso.conf. Add the line "/usr/local/lib", and run ldconfig. Otherwise, the frontend won't find it.

Thanks again,

---

### Post by SpEcIeS on 2005-07-05
[QUOTE=jchristian]

Src installs to a different path than the distro sane, /usr/local/lib, instead of /usr/lib, so you have to edit /etc/ldso.conf. Add the line "/usr/local/lib", and run ldconfig. Otherwise, the frontend won't find it.

[/QUOTE]

Glad it worked out. :D 

When compiling the source one can set the path with the prefix switch. i.e. **./configure --prefix=/usr** Most often than not, I install my compiles to the usual directory */usr*, but it maybe more benificial to install personal compiles to the */usr/local* to differenciate between the two.

---

### Post by hotani on 2007-03-02
So, completely blasting the current installation, then installing everything from source is the only way to go here? I'm staring at the "no device found" error and wondering how much work I want to put into getting this hand-me-down scanner to function.

---

