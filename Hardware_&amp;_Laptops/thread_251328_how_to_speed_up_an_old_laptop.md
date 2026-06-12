---
title: "how to speed up an old laptop"
date: 2006-09-05
forum: Hardware &amp; Laptops
---

### Post by vincent orange on 2006-09-05
Hello,

I've just freshly installed Xubuntu on my HP omnibook laptop. It's working well although I would like some help in speeding it up alittle more.

The specs are:
266Mhz MMX
64Mb Ram
80Gb Hard drive (upgraded from 3GB and theres a noticable speed increase)

I'm using the XFCE desktop manager and disabled anti-antisasing, and other graphic/font smoothing software. I've removed unwanted and unused services from boot to allow for faster bootup. 

Is there anything else I can do to increase performance?
Do you think 64mb Ram is creating a performance bottleneck?

your advice and suggestions will be most welcome.

---

### Post by judgekaster on 2006-09-05
Two suggestions: one, try fluxbox window manager. Two, add some more ram. Up until early this year, I was able to work on a Toshiba 100Mhz notebook using Ubuntu Breezy. But then again, I had 192 MB of RAM.

---

### Post by vincent orange on 2006-09-05
I can get more RAM, maybe get it up to 128Mb, how much faster would it perform?

checking out fluxbox now....

---

### Post by jml on 2006-09-05
I agree with judgekaster.  Increasing the RAM will help a lot because in low ram configuration, Linux will ofter utilize the swap file on your hard drive.  The hard drive is much slower than ram.  I also agree that flux box is also less graphics intensive than XFCE.  Its worth giving it a try.

Joe

---

### Post by vincent orange on 2006-09-05
flux has been dug [http://digg.com/linux_unix/Fluxbuntu_Linux_nBuild1_Alpha_is_Here](http://digg.com/linux_unix/Fluxbuntu_Linux_nBuild1_Alpha_is_Here)

---

### Post by vincent orange on 2006-09-08
okay, ive bought a new 128mb ram module and installed in into the system to give me a total of 192mb of system ram.  One thing i noticed is that the XFCE system didn't bootup any faster with this extra ram, i timed it to be 2 minutes 15 seconds to boot. I guess i may not benefit from fast run time but perhaps more simultaneous open apps.

do you guys think i should install the new flux cd disk or just the window manager?

---

### Post by Macchi on 2006-09-08
I would not expect more RAM to change dramatically the startup time for the  sytem. The bottleneck is probably on moving information from the harddisk to memory an starting up a long sequence of services. This usually takes time if the sequence has not been specifically optimized by removing certain services and starting things in parallel. I believe that current versions of Ubuntu already have some of those optimizations since Dapper starts faster than Breezy etc. 

More RAM will at least allow you to use the system for a while since 64M was unfortunately below any recommended configuration for Ubuntu, as I remember.

Perhahs you could also use this machine as a thin client? Provided it has a good screen and keyboard. Try to install freenx server on a faster machine and the freenx client on your laptop. 

Regarding the installation of "Fluxbuntu" vs simply adding the fluxbox packages: I believe it depends mostly on the available space on your harddisk and if Fluxbuntu has optimizations and good relative stability compared to Ubuntu. Then it would be an advantage to install Flurbuntu from start.

My only recommendation is: If possible, just acquire a new laptop. They are relatively cheap nowadays.



PS: My reserve Laptop is slow with Dapper and somewhat less slow with Xubuntu. That machine is an old laptop with PII 300MHz, 168MB RAM and 40GB HD, with only 800x640 12inch screen and 5 minutes battery time! At least it has a very good keyboard, is very compact and weights 1,9kg. Sincerely, this is only a reserve machine and a backup harddisk. It will be soon moved to my young sons 6 and 4 years old. When providd with a larger battery, two electric motors and some wheels it will become a "robot"! Perhaps I should create a new distribution called "Robuntu" or something similar.;)

---

### Post by vincent orange on 2007-03-16
just to update on my progress, for the benefit of googlers. 

Macchi, I've taken your advice and I'm using the laptop as a thin client using FreeNX, it works quite well and it's found a new use as to let my mum surf the internet and reply to emails. 

As to buying a new laptop, I've done so. I've bought a Lenovo IBM thinkpad R60, it's running a dual boot XP and Ubuntu dapper.

---

