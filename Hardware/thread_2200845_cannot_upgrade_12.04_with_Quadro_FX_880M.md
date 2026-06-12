---
title: "cannot upgrade 12.04 with Quadro FX 880M"
date: 2014-01-21
forum: Hardware
---

### Post by likes2skate on 2014-01-21
I am using kubuntu on a Thinkpad W510 with a Quadro FX 880M display adapter. I can install 12.04 from the CD, no problem. But when I did sudo apt-get dist-upgrade, I ended up with a black screen. I tried several troubleshooting steps I found on the web, all to no avail. 

When I would do X -configure, I would get this:


(++) Using config file: "/root/xorg.conf.new"
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
Number of created screens does not match number of detected devices.
  Configuration failed.
 ddxSigGiveUp: Closing log
Server terminated with error (2). Closing log file.


So I started over, and installed all over again from the 12.04 CD.  

I am afraid to do sudo apt-get dist-upgrade.

What should I do? Thanks

---

### Post by grahammechanical on 2014-01-21
Why do you want to run apt-get dist-upgrade? What does that command give you that the Update Manager or apt-get update + apt-get upgrade does not? My advice is not to use apt-get dist-upgrade unless you have added a PPA and run apt-get update. I am running a version of Ubuntu that is under development and I have found that Update Manager or apt-get upgrade to be sufficient.

[https://help.ubuntu.com/community/AptGet/Howto](https://help.ubuntu.com/community/AptGet/Howto)

Regards.

---

### Post by likes2skate on 2014-01-21
OK, I tried apt-get update + apt-get upgrade, and X is still working.

When I type sudo apt-get upgrade again, I get this:

Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages have been kept back:
  hplip hplip-data libhpmud0 libsane-hpaio linux-generic linux-headers-generic linux-image-generic printer-driver-hpcups printer-driver-hpijs update-notifier-common
0 upgraded, 0 newly installed, 0 to remove and 10 not upgraded.

I was using apt-get dist-upgrade because that would update everything in one step.

This kernel is almost 2 years old. Should I upgrade it? What about the other files that have been kept back?

Thanks,

---

