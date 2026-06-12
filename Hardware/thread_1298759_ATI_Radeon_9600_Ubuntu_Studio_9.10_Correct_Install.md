---
title: "ATI Radeon 9600 Ubuntu Studio 9.10 Correct Installation Help."
date: 2009-10-23
forum: Hardware
---

### Post by WolfRage on 2009-10-23
I am trying to setup my Ubuntu Studio 9.10 fresh install to work with my ATI Radeon 9600 AGP 128mb video card. I found this page ([https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)) and it is my next plan.
But I noticed that at no point does it actually say that I need to apt-get xserver-xorg-video-ati is that correct or should this be a step that I need to take at some point durin the installation?

---

### Post by WolfRage on 2009-10-27
For any one searching for Information relating to a ATI 9600 XT All-In-Wonder I found that your options are as follows: The current best solution is Envy which is aviable in the Ubuntu repositores, this appplication will match up the propritary drivers with your version of Ubuntu, your Kernel and the x-org-server version. 
The next reall good option is to regress to Ubuntu 8.04 Hardy Herron or 8.10 Intrepid.
Although the regression is not ideal it offered me the best solution when coupled with Envy to support the legacy hardware of my older desktop, with out breaking the system with future updates.
Best pages to help you:
This page will give you help with installing drivers on versions of Ubuntu 8.10 and older.
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI) 
This page will tell you how to regress your version of Ubuntu with out reinistalling an older version of Ubuntu.
[http://tan-com.com/posts/technology/fix-ubuntu-904-ati-driver-issue](http://tan-com.com/posts/technology/fix-ubuntu-904-ati-driver-issue)
This is the Envy NG home page, which will help to automagicly update your propritary drivers to your system.
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

