---
title: "Lenovo Ideapad Y450 Webcam issues"
date: 2010-06-23
forum: Hardware
---

### Post by jaywykay on 2010-06-23
Hey guys

I'm new to linux and just installed ubuntu 10.04 for the first time recently. However, there seems to be a problem with my built-in webcam. When I open cheese or skype, it comes out as just a black screen. I had this same issue for a while with windows 7, and was able to resolve it by individually installing the bison driver from the package provided by the lenovo drivers website (when i tried to install the package, it said it could not find the webcam listed in setup.ini and terminated).

I was wondering how i could go about fixing this problem.

I've looked around these forums and the solutions  are either too complicated for me or doesn't seem to apply to my situation. 

My lsusb looks like this:

Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0402:5608 ALi Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

and when i type in ls /dev/video* it comes out like this:

/dev/video0    (and its in yellow font in green space)


Any/all help is appreciated! Thanks!

---

### Post by dino99 on 2010-06-23
[http://www.google.com/search?as_q=y450%2Blucid&hl=fr&num=10&btnG=Recherche+Google&as_epq=&as_oq=&as_eq=&lr=lang_en&cr=&as_ft=i&as_filetype=&as_qdr=m&as_occt=any&as_dt=i&as_sitesearch=&as_rights=&safe=images](http://www.google.com/search?as_q=y450%2Blucid&hl=fr&num=10&btnG=Recherche+Google&as_epq=&as_oq=&as_eq=&lr=lang_en&cr=&as_ft=i&as_filetype=&as_qdr=m&as_occt=any&as_dt=i&as_sitesearch=&as_rights=&safe=images)

---

### Post by jaywykay on 2010-06-24
I don't get it. What am I supposed to do with that link?

---

