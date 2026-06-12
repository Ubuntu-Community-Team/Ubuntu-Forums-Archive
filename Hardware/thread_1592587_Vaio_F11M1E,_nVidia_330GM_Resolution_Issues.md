---
title: "Vaio F11M1E, nVidia 330GM Resolution Issues"
date: 2010-10-10
forum: Hardware
---

### Post by Pacman15 on 2010-10-10
Hello everyone.

I am having some issues with my new Vaio F11M1E/H, i have a nvidia 330GM and I can't get past 800x600. When I install drivers through "Add Aditional Drivers", I won't reach desktop..

Anyone with that sort of problems?

Thanks.

---

### Post by Pacman15 on 2010-10-13
anyone?

---

### Post by xaijin on 2010-10-13
What error do you get exactly? Or is the screen just blank/black?

---

### Post by paulohenrique on 2010-10-13
> **Pacman15 said:**
> Hello everyone.
 
I am having some issues with my new Vaio F11M1E/H, i have a nvidia 330GM and I can't get past 800x600. When I install drivers through "Add Aditional Drivers", I won't reach desktop..
 
Anyone with that sort of problems?
 
Thanks.
 
I'm having problems setting up the video for my Sony Vaio VPCF115FM.
During the install process and after installed, but with the open source drivers, the video resolution is 2048x1536. The monitor native resolution is 1920x1080p (FullHD), but I can set a wide resolution. I tried to set up a lower resolution, but the screen goes even bigger.
I tried to use the additional drivers tool, but then my system stops working with the new driver, giving me a purple screen after the splash. After this point I can't even switch between the TTys (Ctrl + Alt + F*). I think my system really hangs.
The OS is an Ubuntu 10.10 64 bits, clean install and the video card is a NVIDIA GeForce GT **330M.**
I'm not an expert, so I would appreciate to get more information on how to give more datails on the issue.
Thanks in advance,

---

### Post by nuovodna on 2010-10-15
Same here on latest NVIDIA stable driver 260.19.12

Black screen + hard freeze

10.10 + GT 320M

---

### Post by johannesg on 2010-10-15
same computer, excactly the same problem :(, can someone please help us

---

### Post by nuovodna on 2010-10-15
Bug reported here

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/657634](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/657634)

---

### Post by corcomp84 on 2010-10-15
does everyone have the same distro 10.04, I know sometimes it helps to try different live CD's when you have hardware issues.. like 9.10 fixed my problems sometimes.. Its just an option to try..

---

### Post by nuovodna on 2010-10-15
10.04 works fine but in Maverick there is the devil combination of xorg 1.9 + nvidia 260.xx driver  :(

---

### Post by corcomp84 on 2010-10-15
I had a problem with 10.10 finding hardware last night, I wonder if they changed something.. I finally gave up and reinstalled 10.04.. I don't feel that 10.10 was ready yet, but I haven't only installed it twice, it was a 50 % fail rate so far.. I think everyone should call nvidia and complain, that they dont fully support linux.. If we all overwhelmed there tech services then maybe they would do something..

---

### Post by nuovodna on 2010-10-15
you can download nvidia*-256*.deb packages for maverick here and block the version

64bit : 
[https://launchpad.net/ubuntu/maverick/amd64/nvidia-current/256.53-0ubuntu3](https://launchpad.net/ubuntu/maverick/amd64/nvidia-current/256.53-0ubuntu3)



i386:
[https://launchpad.net/ubuntu/maverick/i386/nvidia-current/256.53-0ubuntu3](https://launchpad.net/ubuntu/maverick/i386/nvidia-current/256.53-0ubuntu3)

---

### Post by saliflo on 2010-10-16
> **nuovodna said:**
> you can download nvidia*-256*.deb packages for maverick here and block the version

64bit : 
[https://launchpad.net/ubuntu/maverick/amd64/nvidia-current/256.53-0ubuntu3](https://launchpad.net/ubuntu/maverick/amd64/nvidia-current/256.53-0ubuntu3)



i386:
[https://launchpad.net/ubuntu/maverick/i386/nvidia-current/256.53-0ubuntu3](https://launchpad.net/ubuntu/maverick/i386/nvidia-current/256.53-0ubuntu3)

At last! Many thanks. Indeed before I tried to install 256 as .run file and and I thought I did it, It looks like it was a mistake. But now 3D is OK. 
Repository driver and maverick aren't match, is it strange?

---

### Post by recontitter on 2010-10-16
Hi,
I resolved this issue going to recovery mode at boot, removing nvidia driver through Add/Remove Programs and than I quit xserver, changed to telinit3 in terminal, than I've just installed common driver from nvidia website by hand - like sh ./Nvidia***.sh and it works fine.
Altough it is possible that nvidia installer overwrite xorg.conf file and there is no need to uninstall driver shipped with ubuntu 10.10 (which apparently is faulty).

Regards,
Wojtek

---

### Post by earthmeLon on 2010-10-22
When I upgraded from 10.4 to 10.10 my xorg.conf file got destroyed.

Check here for good information:
[http://code.google.com/p/vaio-f11-linux/wiki/NVIDIASetup](http://code.google.com/p/vaio-f11-linux/wiki/NVIDIASetup)

Install a working driver

Re-set your xorg conf:
$ nvidia-xconfig

Add any additional lines you may need (from prev link)

---

