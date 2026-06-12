---
title: "Many blank screens on Asus K42J - Geforce 310M"
date: 2010-08-24
forum: Hardware
---

### Post by FariAzz on 2010-08-24
Hi all,

I'm trying to get Ubuntu 10.04 working on my Asus K42J, I installed and it works ok without installing proprietary drivers, if I install the NVidia drivers recommended by Ubuntu then I get a blank screen instead of the login screen.

All the workarounds I've read for my graphic card involve accessing the Recovery Mode from the GRUB menu, but here is the thing, that mode leads me to a blank screen **whether I install the proprietary drivers or not**. The workarounds I've read about can be found in:


[http://ubuntuforums.org/showthread.php?t=1392766&page=2](http://ubuntuforums.org/showthread.php?t=1392766&page=2)   (post 18  )

[http://samiux.blogspot.com/2010/05/howto-fix-blank-screen-on-ubuntu-1004.html](http://samiux.blogspot.com/2010/05/howto-fix-blank-screen-on-ubuntu-1004.html)

[http://ubuntuforums.org/showthread.php?t=1470822](http://ubuntuforums.org/showthread.php?t=1470822)

Some solutions involve accessing Recovery Mode to manually install the drivers from the NVidia's website, but I can't try any of this since I can't access the Recovery Mode.

I've reinstalled Ubuntu twice trying to get this working, any help would be very appreciated.

More info:
-Ubuntu 10.04 AMD64
-Laptop ASUS K42J , Nvidia GeForce 310M, Intel i5 450, 4 GB ram

Cheers

[UPDATE] I install the Nvidia drivers from Nvidia's website (GeForce 310M linux 64) using the Live CD, but I got the blank screen afterwards in my Ubuntu installation, so I had to reinstall it for the third time....

---

### Post by saeed_s58 on 2010-09-04
> **FariAzz said:**
> Hi all,

I'm trying to get Ubuntu 10.04 working on my Asus K42J, I installed and it works ok without installing proprietary drivers, if I install the NVidia drivers recommended by Ubuntu then I get a blank screen instead of the login screen.

All the workarounds I've read for my graphic card involve accessing the Recovery Mode from the GRUB menu, but here is the thing, that mode leads me to a blank screen **whether I install the proprietary drivers or not**. The workarounds I've read about can be found in:


[http://ubuntuforums.org/showthread.php?t=1392766&page=2](http://ubuntuforums.org/showthread.php?t=1392766&page=2)   (post 18  )

[http://samiux.blogspot.com/2010/05/howto-fix-blank-screen-on-ubuntu-1004.html](http://samiux.blogspot.com/2010/05/howto-fix-blank-screen-on-ubuntu-1004.html)

[http://ubuntuforums.org/showthread.php?t=1470822](http://ubuntuforums.org/showthread.php?t=1470822)

Some solutions involve accessing Recovery Mode to manually install the drivers from the NVidia's website, but I can't try any of this since I can't access the Recovery Mode.

I've reinstalled Ubuntu twice trying to get this working, any help would be very appreciated.

More info:
-Ubuntu 10.04 AMD64
-Laptop ASUS K42J , Nvidia GeForce 310M, Intel i5 450, 4 GB ram

Cheers

[UPDATE] I install the Nvidia drivers from Nvidia's website (GeForce 310M linux 64) using the Live CD, but I got the blank screen afterwards in my Ubuntu installation, so I had to reinstall it for the third time....

Hi
I've faced with a similar problem with the 32-bit version of ubuntu 10.04 on my K42JC ASUS Laptop. After googling on my problem saw your statement here. finally I resolved the problem and decided to report some points here, which may be helpful for some others.
After the completion of my ubuntu installation I noticed that I can't have any access to my ttys by CTRL+ALT+F(1-6). So decided to follow the ubuntu detection of the nvidia driver. But after doing that, I loosed all of the access to my system (even with the recovery mode).
Then I decided to come up on my system using the i915.modset=0 grub boot argument (using "e" and then editing using arrow keys on the ubuntu option in the grub boot list when the system is coming up). Then I installed the openssh (server) on my system and then connect to the system using ssh on other node in the private network (you can do that also using your Desktop PC and a cross network cable between laptop and Desktop PC). At this point I assured that my lovely textmode connection to the laptop is stablished. from now on, I downloaded the appropriate nvidia driver from their site for linux. then purged the installed driver using apt-get. after that I install the new driver from the ssh-provided command-line after stopping the gdm service. after all I noticed that the problem remains at the same state.
After all I changed the xorg configuration file using "X -configure" (or may be Xorg -configure [unfortunately I've lost the details now; I'll try to edit this later]) command and then started the gdm and everything turns up!
I think that it may work also with that ubuntu-installed drivers.

---

### Post by raghuramos1987 on 2010-09-04
> **saeed_s58 said:**
> Hi
I've faced with a similar problem with the 32-bit version of ubuntu 10.04 on my K42JC ASUS Laptop. After googling on my problem saw your statement here. finally I resolved the problem and decided to report some points here, which may be helpful for some others.
After the completion of my ubuntu installation I noticed that I can't have any access to my ttys by CTRL+ALT+F(1-6). So decided to follow the ubuntu detection of the nvidia driver. But after doing that, I loosed all of the access to my system (even with the recovery mode).
Then I decided to come up on my system using the i915.modset=0 grub boot argument (using "e" and then editing using arrow keys on the ubuntu option in the grub boot list when the system is coming up). Then I installed the openssh (server) on my system and then connect to the system using ssh on other node in the private network (you can do that also using your Desktop PC and a cross network cable between laptop and Desktop PC). At this point I assured that my lovely textmode connection to the laptop is stablished. from now on, I downloaded the appropriate nvidia driver from their site for linux. then purged the installed driver using apt-get. after that I install the new driver from the ssh-provided command-line after stopping the gdm service. after all I noticed that the problem remains at the same state.

I also did this much and got frustrated when it did not get resolved.

> **saeed_s58 said:**
> 
After all I changed the xorg configuration file using "X -configure" (or may be Xorg -configure [unfortunately I've lost the details now; I'll try to edit this later]) command and then started the gdm and everything turns up!


Could you please post what you did to configure it? Thanks

> **saeed_s58 said:**
> 
I think that it may work also with that ubuntu-installed drivers.

---

### Post by saeed_s58 on 2010-09-05
> **raghuramos1987 said:**
> 
Could you please post what you did to configure it? Thanks

Hi
The X -configure command created an appropriate xorg.conf file in my case. And what I did only using the ssh to have a text-mode access to my linux box and running X -configure command after stopping gdm and then starting gdm after the manipulation of xorg.conf file.

---

