---
title: "GNUCash with HBCI and aqofxconnect enabled"
date: 2008-07-26
forum: General Help
---

### Post by Mercurio82 on 2008-07-26
I managed to compile GNUCash with HBCI and aqofxconnect in Kubuntu 7.10 using the instructions on the GNUCash website. 

I use Kubuntu using VMWare fusion and unfortunately my virtual machine crashed and I had to start again.

I decided to upgrade to Kubuntu 8.04 but I was unable to successfuly compile gnucash. The instructions are out of date as libaqbanking16-dev aqbanking16-qt-wizard have been replaced by libaqbanking20-dev and there is no aqbanking16-qt-wizard. 

So I went back to 7.10 and compiled and installed from there.

I would like to use Kubuntu 8.04 so I copied the compiled apps to 8.04 and tried to install but it refuses saying there are dependancy problems and that I need to install libaqbanking16, libofx3 and libgwenhywfar38.

When I try to install them it says those packages are not available.

Not sure what to do next. Is it ok to install those packages? How would I do that? Do I enable old repositories?

Alternatively, if someone knows how to update the gnucash wiki instructions for 8.04 then I could try to compile using the latest libraries. 

[http://wiki.gnucash.org/wiki/Debian](http://wiki.gnucash.org/wiki/Debian)

I have spent ages trying to get this to work and would greatly appreciate any help.


Thanks

---

### Post by tgerbert on 2008-07-26
I had some headaches getting GnuCash 2.2.5 w/OFX & HBCI to compile on Ubuntu 8.04.

I ended up going to [http://packages.debian.org/](http://packages.debian.org/) and manually downloading/installing the packages it complained about.

---

