---
title: "Unbuntu 10.04 Won't run on my netbook anymore!"
date: 2010-07-01
forum: Hardware
---

### Post by nero100 on 2010-07-01
Basically what happened guys is that i dropped my netbook on the floor while it was turned on when i went to pick it up it was turned off and when i rebooted my system it says this. mount: mouting /dev/disk/by-uuid/4fdc900-05d6-4d96-8476-a96d0489373f on /root failed: invalid argument mount mounting /dev on /root/dev failed: No such file or directory mount mounting /sys on /root/sys failed: No such file or directory mount mounting /proc on /root/proc failed: No such file or directory mount mounting /sys on /root/sys failed: No such file or directory 
 
BusyBox v1.13.3 (ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash) 
 
I have also tried too boot ubuntu live test and it will not allow me and it also will not let me re-install it does anybody have any idea have i can fix this?
 
Thanks in advance guys!

---

### Post by AltomineUK on 2010-07-05
Sounds like your hard drive took the brunt of the force. Normally, when your PC has been forcefully shut down Linux often attempts a quick check of the filesystem to make sure of its integrity. From your description, the read error seems to imply that your hard-drive has had it. 

Are you able to create and boot from a liveCD or a liveUSB?

---

