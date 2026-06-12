---
title: "Hard drive light on my laptop won't stop blinking"
date: 2010-07-01
forum: Hardware
---

### Post by rogue780 on 2010-07-01
I installed Ubuntu 10.04 on my [MSI GX630]("http://www.newegg.com/product/product.aspx?item=n82e16834152073"). Vanilla install and my hard drive light keeps flashing and won't stop. I sudo apt-get upgrade'd the system, restarted. It's keeps trashing.

I read an old thread about 7.10 where someone installed laptop-mode and that fixed the problem...but alas, it is no longer in the repository.

Nothing is overtaxing the CPU either. Here is part of the top output:

>   PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                         
 1749 root      20   0 60268  45m  15m S    7  1.5   3:22.73 Xorg                                                                            
 2372 shawn     20   0 59696  45m  15m S    3  1.5   1:27.85 compiz                                                                          
 9518 shawn     20   0 45768  13m 9.9m R    3  0.4   0:02.06 gnome-terminal                                                                  
23159 shawn     20   0 58476  20m  12m S    2  0.7   1:07.38 xchat                                                                           
  885 messageb  20   0  3292 1652  760 S    2  0.1   2:12.94 dbus-daemon                                                                     
 2651 root      20   0 15660 3040 2432 S    2  0.1   2:42.99 udisks-daemon                                                                   
 2613 shawn     20   0  8104 3544 2576 S    1  0.1   2:00.66 gvfs-gdu-volume                                                                 
 2748 shawn     20   0 19272 7484 5740 S    1  0.2   1:23.41 gdu-notificatio                                                                 
 5081 shawn     20   0  341m  83m  27m S    1  2.8   2:44.32 firefox-bin                                                                     
 5605 shawn     20   0 35556  11m 8972 S    1  0.4   1:21.85 update-notifier                                                                 
15573 root      18  -2  2544  976  344 S    1  0.0   1:11.39 udevd                                                                           
    1 root      20   0  2800 1624 1164 S    0  0.1   0:22.91 init                                                                            
28235 shawn     20   0  2544 1232  904 R    0  0.0   0:00.99 top                                                                             
 

Help!

---

### Post by tgalati4 on 2010-07-01
Could be indexing going on.  There are several databases that need to be created for a new install.  Put a piece of electrical tape over the LED.  It won't bother you so much.

---

### Post by rogue780 on 2010-07-05
> Put a piece of electrical tape over the LED. It won't bother you so much.

That's kind of a akin to telling someone not to hold their iphone 4 in their left hand...

I have ubuntu 10.04 installed on 3 other computers and I don't get this kind of hard drive activity...It's a problem that only affects my laptop and quite frankly it is shortening the life of my hard drive. It shouldn't have THAT much to index...it was a fresh install. All i've added was eclipse and the jdk.

---

