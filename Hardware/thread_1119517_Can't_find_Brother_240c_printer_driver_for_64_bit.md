---
title: "Can't find Brother 240c printer driver for 64 bit"
date: 2009-04-08
forum: Hardware
---

### Post by sofasurfer on 2009-04-08
I have 64 bit cpu and Ubuntu (8.10). I went to the Brother website and downloaded lpr and cups drivers. At [http://solutions.brother.com/linux/en_us/instruction_prn3.html#dpkg1](http://solutions.brother.com/linux/en_us/instruction_prn3.html#dpkg1) I followed the "Install LPR driver (dpkg)" section and this was the result...

```

terry@ubuntu:~$ sudo dpkg -i --force-all --force-architecture dcp540cnlpr-1.0.1-1.i386.deb
[sudo] password for terry: 
terry@ubuntu:~/Desktop$ sudo dpkg -i --force-all --force-architecture mfc240clpr-1.0.1-1.i386.deb
dpkg - warning, overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 116928 files and directories currently installed.)
Preparing to replace mfc240clpr 1.0.1-1 (using mfc240clpr-1.0.1-1.i386.deb) ...
Unpacking replacement mfc240clpr ...
Setting up mfc240clpr (1.0.1-1) ...
mkdir: cannot create directory `/var/spool/lpd/mfc240c': No such file or directory
chown: cannot access `/var/spool/lpd/mfc240c': No such file or directory
chgrp: cannot access `/var/spool/lpd/mfc240c': No such file or directory
chmod: cannot access `/var/spool/lpd/mfc240c': No such file or directory

```

Am I to understand that there is no driver for 64 bit? What should I do?
Thanks

---

### Post by sofasurfer on 2009-04-08
lso tried making sense out of [https://wiki.ubuntu.com/BrotherDriverPackaging](https://wiki.ubuntu.com/BrotherDriverPackaging) but even though my Brother 240c is listed under the bh7 section (what ever that is) but have still had no luck.

Sure would appreciate hearing from a successful 240c installer.

Thanks...

---

### Post by Nukinfuts on 2009-04-08
check out [http://www.openprinting.org/](http://www.openprinting.org/)

---

### Post by sofasurfer on 2009-04-09
So far I am not able to make any progress. I even tried installing the windows drivers under wine with no luck. Although I think I came close. I end up with an error saying to restart the computer and make sure all apps are closed and then finish the installation but this is as far as it gets.
Hmmmm.....

---

### Post by Ruhani04 on 2009-04-25
There are some instructions for ubuntu 8.10 you need to follow them first according to brother before installation.

[http://solutions.brother.com/linux/en_us/before.html](http://solutions.brother.com/linux/en_us/before.html)

[http://solutions.brother.com/linux/en_us/faq_prn.html#142](http://solutions.brother.com/linux/en_us/faq_prn.html#142)

I'm using an AMD64 bit version of Linux. Can I use the Brother Linux printer drivers? 

Yes. Our drivers are created and optimized for 32 bit version of Linux,
but those can be used for 64 bit Linux also. Some additional steps are required.


For dpkg users:
1. Install lib32stdc++6(Debian) or ia32-libs(Ubuntu)
2. Restart the system
3. Use "--force-architecture" option when you install the drivers.
4. After the driver installation, and if there is "/usr/lib64/filter/", copy the file which name starts with "brlpdwrapper" ( in the "/usr/lib/cups/filter/" ) to "/usr/lib64/cups/filter/". 
Or confirm there are symbolic links between "/usr/lib/" and "/usr/lib64/".

Good Luck !;)

---

