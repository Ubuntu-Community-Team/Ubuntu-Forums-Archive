---
title: "Problems with ati drivers Ubuntu 12.10 x64"
date: 2012-11-15
forum: Hardware
---

### Post by TPAKTOPUCTA on 2012-11-15
Dear all,
I have the following issue with my installation of ubuntu 12.10 x64. This morining I did the stupied thing to download the latest version of ati video drives (i am using a toshiba laptop with ati radeon hd 6400 video card) and to tried to install them in my environment. During the installtion I received a message that old versions of the driver present and I need to reinstall it. So I followed steps explained in the forum:
sudo sh /usr/share/ati/fglrx-uninstall.sh 
sudo apt-get remove --purge fglrx fglrx_* fglrx-amdcccle* fglrx-dev*
and I received an error. Than my nightmare began.

The unity did not work, and I was able to usi only terminal to use the system. After installing again the fgrlx (sudo apt-get install fglrx) at least the unity is running, but my laptop is not working in normaln resolution (and I cannot changed it). In addition I can see that there is a problem with the video driver so I searched over the internet possible solutions but without any luck. So that is why I decided to sekk help here. Please if anyone could help I would be very thankful.

Regards,

---

### Post by TPAKTOPUCTA on 2012-11-16
After hours of searching I found this link (how to install default drivers for ATI) [http://askubuntu.com/questions/74171/is-my-ati-graphics-card-supported-in-ubuntu](http://askubuntu.com/questions/74171/is-my-ati-graphics-card-supported-in-ubuntu) and this solve my problems.

---

### Post by friTTe81 on 2012-11-16
Hmm i have the 5650 card and i tried installing only to end up with borkage hehe, so now im staying with the open source ones.

---

