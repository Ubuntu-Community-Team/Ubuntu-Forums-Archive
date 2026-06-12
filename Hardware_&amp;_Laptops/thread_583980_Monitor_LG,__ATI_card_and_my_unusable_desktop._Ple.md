---
title: "Monitor LG,  ATI card and my unusable desktop. Please help"
date: 2007-10-20
forum: Hardware &amp; Laptops
---

### Post by user_1977 on 2007-10-20
I've installed UBUNTU 7.10 (64 bit) on my pc some day ago.
I've an AMD Opteron, ATI Radeon 9600XT and Monitor LCD lg flatron L1915S.

From the first time I run UBUNTU I saw something was strange.
I can stay more than 10 minutes reading on my desktop because my desktop is too luminous but also changing my wallpaper , my theme and LCD settings , I continue to suffer with my eyes....
:(:(:(:(

I don't know what to do.
The system has recognized my monitor as plug 'n play and I tried also to set the refresh value supported by the monitor. Also LCD PANEL 1280x1024 on the monitor settings. Also using the automatic settings of the monitor

:(:(:(:(

**please help !!!!**

---

### Post by user_1977 on 2007-10-20
:(

---

### Post by user_1977 on 2007-10-21
:(:(

---

### Post by user_1977 on 2007-10-21
Can depend by the DVI connector ? :confused:

---

### Post by drama1981 on 2007-10-21
its the stock ati driver. there are numerous problems with this driver. some users have some issues some others. my solution would either be to downgrade xserver-xorg-ati to a version from fiesty. you can also try the fglrx driver (this is the propriatory ati driver). easiest way to try fglrx is to look under system/restriced manager. if it lists ati check that box. it will d/l a few packages. 3 i think. then ask for a restart. now im not gonna promise you that the fglrx driver will work with that card as certain cards arent supported. but you can give it a try. hope this works. cheers :)

p.s. if you do try fglrx and x refuses to boot. you will end up in a shell just type your username and pass 

and do 

sudo dpkg-reconfigure xserver-xorg

when it asks for driver choose ati. follow through with the rest of the config. then do 

sudo /etc/init.d/gdm restart

this will restart x

note: reconfigureing is only nessesary if x doesnt start on its own after reboot.

---

