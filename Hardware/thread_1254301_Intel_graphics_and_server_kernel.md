---
title: "Intel graphics and server kernel?"
date: 2009-08-31
forum: Hardware
---

### Post by arcull on 2009-08-31
Hi there. I'm a brand new user of ubuntu, but already have some experiences from suse. I decided to put kubuntu 9.04 on my new laptop acer emachines g725 since from experiences from live cd it looked the most suitable, I mean it did detect the most of it's hardware (wireless, sound,...) and testing with glxgears gave the best result (around 900 fps). So I've installed it and am pretty happy with it. However I've encountered the first issue. Since my laptop has 4Gb of ram, I installed also server kernel ```
uname -a
Linux Stol 2.6.28-15-server #49-Ubuntu SMP Tue Aug 18 19:30:06 UTC 2009 i686 GNU/Linux
```, but unfortuntelly graphics running server kernel is very bad, running glxgears from konsole I get just around 200 fps. Here is some more info about hardware ```
lspci |grep Graphic
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 09)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 09)
```. Installed driver is 2:2.6.3. So my qustion is if this can be solved somehow, since I would like to use all of my 4GB memory. Thanks in advance for any help you can provide.

---

### Post by arcull on 2009-09-01
No clue :( ok, someone maybe knows where could I find prebuilt 32-bit kernels for 9.04 with PAE support, thanks

---

### Post by PatrickVogeli on 2009-09-01
Look here [http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)

And **DoNotTrustGlxGears**

---

### Post by arcull on 2009-09-01
PatrickVogeli thanks, but I decided to give x64 version a try, that should increase all performance in general.

---

### Post by arcull on 2009-09-02
Now with x64 version of Jaunty, graphics even better than on 32bit, and so far no probs :)

---

### Post by checoimg on 2009-09-02
I did 
code:

sudo apt-get install linux-server linux-headers-server linux-restricted-modules-server 

This installed the server kernel and got 3.9 GB RAM

---

### Post by arcull on 2009-09-02
> I did 
code:

sudo apt-get install linux-server linux-headers-server linux-restricted-modules-server 

This installed the server kernel and got 3.9 GB RAM yeah I know that, but server kernel for some reason doesn't work well with my graphic card, even though drivers were installed ok. However I've put on now x64 destkop edition and am satisfied with both, graphics and amount of ram :)

---

