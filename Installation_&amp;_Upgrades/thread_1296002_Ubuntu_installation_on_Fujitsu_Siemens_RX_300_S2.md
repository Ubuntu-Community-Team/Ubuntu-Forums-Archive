---
title: "Ubuntu installation on Fujitsu Siemens RX 300 S2"
date: 2009-10-20
forum: Installation &amp; Upgrades
---

### Post by ionutneicu on 2009-10-20
Hi everybody !
I have one Fujitsu Siemens RX 300 S2 server and I decided to install Ubuntu using Ubuntu Minimal image.
I've set-up the Raid5 logical group and installer worked fine, automatically downloaded and installed MegaRaid drivers.  After finish installing operating sistem, at first boot, grub failed to load Ubuntu.
The boot messages shown on screen looks like :

[B]
Boot from ( hd0,0 ) ext3 89f4.................
Starting up
Loading, please wait
Gave up waiting for root device. Common problems :
- Boot args
    - Check root delay = ( did system wait long enough ? )
    - Check root  = ( did system wait for right device ? )
-Missing modules ( cat /proc/modules; ls /dev )

ALERT ! /dev/disk/by-uuid/89f4.........[/B]**.......    does not exists**

in /dev/disk I haven't a "by-uuid" folder.
in /proc/modules i have a "megaraid" module


Any ideas ?

---

### Post by snake_eyes on 2009-10-21
Hello,

Thank you for emailing me and I'm glad to share my information with you regarding to this matter.

Actually I got the same error before, but in order to avoid it and because I must install the ubuntu on the mashine for the reason that the was down, I didn't instdall the Raid5 unlike Windwos, in case you wanna insall windows you must first boot from the startup CD of the Siemens and setup the Raid5  etc... in our case I wanna install the Ubuntu I booted directelly from the ubutnu CD's and installed it.

Altouh I'm working on it since 14 months with Ubuntu 8.4 and I have another server went online last month without any problem.

Please note that if you server has more thatn 4 GB (10,12,24,32 etc...) of RAM the ubutnu will dedect them as 4 that is easy to fore Ubuntu to read them no problem you just install the OS and email me your contact email address and we can continue...

Cheers,

---

