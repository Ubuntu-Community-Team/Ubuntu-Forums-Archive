---
title: "installation of ATI driver failed"
date: 2012-08-06
forum: Hardware
---

### Post by hani270 on 2012-08-06
when i try to install ATI driver from "Additional Drivers" i see this error :

[IMG]http://i1045.photobucket.com/albums/b456/badstuber/Screenshotfrom2012-08-06124431.png[/IMG]

my laptop: DELL inspiron n 4030

Graphic Card: 512MB ATI Card -- Mobility Radeon HD 5430 Series 
CPU: Intel® Core&#8482; i3 CPU M 370 @ 2.40GHz × 4 
RAM: 4GB

---

### Post by KaizerLinux on 2012-08-06
+1

I had the same issue with my ATI Radeon HD 5700. I could install the first one, but not the one marked "(post-release updates)". Though running on the older one works for me.

---

### Post by propercoil on 2012-08-06
When i install the second driver and then try to invoke "fglrxinfo" i get multiple errors. i tried to install the propriety driver from amd following [this]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI") [this]("http://askubuntu.com/questions/124292/what-is-the-correct-way-to-install-ati-catalyst-video-drivers") and [this]("http://askubuntu.com/questions/81344/how-to-fix-error-with-ati-driver-error-of-failed-request") but nothing works and when rebooting you get a message saying ubuntu running on low graphics, catalyst crashes every time. now i'm stuck trying to uninstall fglrx with the errors:

sudo apt-get remove --purge fglrx fglrx_* fglrx-amdcccle* fglrx-dev* xorg-driver-fglrx

[sudo] password for propercoil: Reading package lists... Done Building dependency tree
Reading state information... Done Virtual packages like 'xorg-driver-fglrx' can't be removed E: Unable to locate package fglrx_8.980-0ubuntu1_i386.deb E: Couldn't find any package by regex 'fglrx_8.980-0ubuntu1_i386.deb' E: Unable to locate package fglrx- amdcccle_8.980-0ubuntu1_i386.deb E: Couldn't find any package by regex 'fglrx- amdcccle_8.980-0ubuntu1_i386.deb' E: Unable to locate package fglrx-dev_8.980- 0ubuntu1_i386.deb E: Couldn't find any package by regex 'fglrx-dev_8.980-0ubuntu1_i386.deb'

This is beyond crazy, installing a popular graphics driver( Radeon HD5400) takes ages when on windows it auto detects it. I'm not looking for out of the box compatibility of course from a linux os but even a very technical oriented person can't solve simple things that should have been dealt with years ago.

---

