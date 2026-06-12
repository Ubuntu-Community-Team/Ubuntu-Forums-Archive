---
title: "aMSN install problems"
date: 2008-07-24
forum: General Help
---

### Post by bunny_basher on 2008-07-24
Hi, Im trying to install the latest version of aMSN as the version i have wont sing in anymore :confused: but i get this....

Checking for required C library versions ... OK
Error: Unable to prepare package AMSN MSN client.

I have tcl 8.5 installed and i am using the 8.5 (amsn-0.97.1-1.tcl85.x86.package) installer - i dont know what i am doing wrong! lol

Cheers, Marcus

---

### Post by DJTurboToJo on 2008-07-31
You should be able to enter a password at the beginning of the installation. It says it needs this password in order to get root privileges, so that amsn can be installed. If you enter no password the screen that you were describing pops up. 

Anyhow, the installation didnt work at my pc. And so I'm still using version 0.97 (the version that also can be installed using the package manager).

---

### Post by DJTurboToJo on 2008-07-31
So, I tried to use 0.97 to connect but this was not successful. So, I checked whats going on and there was quite an important change:

[http://article.gmane.org/gmane.network.instant-messaging.amsn.devel/9544](http://article.gmane.org/gmane.network.instant-messaging.amsn.devel/9544)

That means you have to install 0.97.1: Out of my experience the generic installer didnt work (maybe it works on your computer):

[http://prdownloads.sourceforge.net/amsn/amsn-0.97.1-1.tcl85.x86.package](http://prdownloads.sourceforge.net/amsn/amsn-0.97.1-1.tcl85.x86.package)

but installing it from a tar ball did succeed:

[http://prdownloads.sourceforge.net/amsn/amsn-0.97.1.tar.bz2](http://prdownloads.sourceforge.net/amsn/amsn-0.97.1.tar.bz2)

The steps are pretty easy:
1) download
2) tar -xvjf amsn-0.97.1.tar.bz2
3) ./configure
4) make
5) sudo make install


(from: [http://amsn-project.net/wiki/Installing_Tarball](http://amsn-project.net/wiki/Installing_Tarball))


EDITED: use this patch to get nice fonts
   [http://patches.ubuntu.com/a/amsn/extracted/01_patching_amsn.dpatch](http://patches.ubuntu.com/a/amsn/extracted/01_patching_amsn.dpatch)
(from: [http://www.amsn-project.net/forums/viewtopic.php?p=31395](http://www.amsn-project.net/forums/viewtopic.php?p=31395))

---

### Post by ant1060 on 2008-08-06
Hi
Could you please tell me (in easy language :)) HOW to use the patch provided to get the nice fonts?  
Thanks!

---

### Post by tuxxy on 2008-08-06
MSN changed their protocol, you dont need to install from source, you should be using the supported package of the new aMSN version 0.97.2 which is available for 32/64bit download here [http://www.getdeb.net/app/aMSN](http://www.getdeb.net/app/aMSN) 

Once you downloaded to desktop right click on the file and select install.

---

