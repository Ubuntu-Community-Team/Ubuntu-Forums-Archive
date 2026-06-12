---
title: "Help required for fixing screen resolution for SONY VAIO PCG-21314w"
date: 2011-06-02
forum: Hardware
---

### Post by connecttomyworld on 2011-06-02
I recently installed ubuntu 11.04 on my netbook SONY VAIO PCG-21314w. However, the default screen resolution doesnot match with resolution of netbook which I think is 1350x768.
is there some way to change it?
I tried help given in thread [http://ubuntuforums.org/showthread.php?t=1762101](http://ubuntuforums.org/showthread.php?t=1762101) but could not succeed as I could not generate xorg.conf as per instructions given in the thread [http://ubuntuforums.org/showthread.php?t=1336863](http://ubuntuforums.org/showthread.php?t=1336863). 
The following is the screen output:[INDENT][INDENT] [I]sony@ubuntu:~$ sudo service gdm start
[sudo] password for sony: 

Warning: Fake initctl called, doing nothing.
sony@ubuntu:~$ sudo Xorg -configure

Fatal server error:
Server is already active for display 0
    If this server is no longer running, remove /tmp/.X0-lock
    and start again.


Please consult the The X.Org Foundation support 
     at [http://wiki.x.org](http://wiki.x.org)
 for help. 

 ddxSigGiveUp: Closing log
sony@ubuntu:~$ sudo service gdm stop

Warning: Fake initctl called, doing nothing.
sony@ubuntu:~$ 
[/I][/INDENT][/INDENT]Any help possible.
Thanks in advance

---

