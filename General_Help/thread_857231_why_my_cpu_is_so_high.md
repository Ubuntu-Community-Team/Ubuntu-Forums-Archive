---
title: "why my cpu is so high"
date: 2008-07-12
forum: General Help
---

### Post by endswel on 2008-07-12
[PHP]  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                                             
 5078 root      20   0  446m  99m  15m R 59.4  9.9  22:34.59 Xorg                                                                                                                
 5629 endswel   20   0  636m 155m  31m S  6.5 15.4   7:03.55 firefox                                                                                                             
10043 endswel   20   0  213m  24m  14m S  4.5  2.5   0:06.80 gnome-system-mo                                                                                                     
 5557 endswel   20   0  212m  22m 6596 S  1.5  2.2   1:02.77 compiz.real                                                                                                         
10059 endswel   20   0  241m  20m  10m R  1.5  2.0   0:00.54 gnome-terminal                                                                                                      
 6400 endswel   20   0 59184  14m 8160 R  1.3  1.4   2:44.86 npviewer.bin                                                                                                        
 5484 endswel   20   0  327m  29m  16m S  0.5  3.0   0:34.31 gnome-panel                                                                                                         
    1 root      20   0  4020  876  592 S  0.0  0.1   0:01.12 init                                                                                                                
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd                                                                                                            
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0                                                                                                         
    4 root      15  -5     0    0    0 S  0.0  0.0   0:00.10 ksoftirqd/0                                                                                                         
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0                                                                                                          
    6 root      15  -5     0    0    0 S  0.0  0.0   0:00.16 events/0                                                                                                            
    7 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khelper                                                                                                             
   39 root      15  -5     0    0    0 S  0.0  0.0   0:00.02 kblockd/0                                                                                                           
   42 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid                                                                                                              
   43 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify                                                                                                        
  154 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kseriod                                                                                                             
endswel@endswel-desktop:~$ 0    0    0 S  0.0  0.0   0:00.06 pdflush [/PHP]  


sometimes the pid=5078's cpu is 67% more.
I do not know why,
Do sb. know it ? and help me, I am a newer in ubuntu
what is that me, why i open the ff3, and open some web page, like now, i just run ff3, and look at the top, it's the result.

CPU : AMD Sempron 2800+ RAM&#65306; 1G  SWAP&#65306; 1G

---

### Post by Polygon on 2008-07-12
xorg seems to be the one sucking all your cpu usage, and if it was firefox (or flash for that matter) it would say firefox was using all the cpu...

ive googled some and some people say it could be a problem with the video drivers, are you running the latest version of your drivers? what is your video card, and are you using the binary drivers or the oss ones?

---

### Post by endswel on 2008-07-12
ati video card
is that the main problem?

i do not install any ati driver, use the system default

if it is the driver problem, how can i do?

where can i do on the google, search the special one of the driver to suit the ati video card? 

my system is ubuntu 8.04.

---

