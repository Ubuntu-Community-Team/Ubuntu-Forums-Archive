---
title: "login issues"
date: 2007-04-09
forum: Hardware &amp; Laptops
---

### Post by cosmo18 on 2007-04-09
I installed ubuntu edgy on my mom's laptop for her and it was working fine, but when she rebooted it, it comes up with the login screen. but when she puts in her username and password and hits enter it comes up with the activity icon like it's booting in but then the screen flashes and it goes right back to the bootin screen, I made sure that the caps lock key was not on, now I am stumped why this is not working

---

### Post by taurus on 2007-04-09
Let's check for disk space.  Boot into recovery mode from GRUB menu and at the prompt, post the output of this command here.

```
df -h
```

---

### Post by cosmo18 on 2007-04-09
it says 
Filesystem                   Size     Used     Avail     Use%     Mounted on
/dev/hdc3                     2.9G     2.9G      0            100%     /
varrun                           363M    16k        363M        1%     /var/run
varlock                          363M        0        363M         0%    /var/lock
procbususb                    10M     88K         10M        1%    /proc/bus/usb
udev                                10M     88K          10M        1%    /dev
devshm                        363M         0        363M         0%   /dev/shm
lrm                                 363M    18M       346M        5%    /lib/modules/2.6.17-11-generic/volatile
/dev/hdc2                      7.7G   129M        7.2G         2%   /media/hdc1

---

### Post by cosmo18 on 2007-04-09
it says 
```
Filesystem                   Size     Used     Avail     Use%     Mounted on
/dev/hdc3                     2.9G     2.9G      0            100%     /
varrun                           363M    16k        363M        1%     /var/run
varlock                          363M        0        363M         0%    /var/lock
procbususb                    10M     88K         10M        1%    /proc/bus/usb
udev                                10M     88K          10M        1%    /dev
devshm                        363M         0        363M         0%   /dev/shm
lrm                                 363M    18M       346M        5%    /lib/modules/2.6.17-11-generic/volatile
/dev/hdc2                      7.7G   129M        7.2G         2%   /media/hdc1
```

---

### Post by AkiraXXX on 2007-04-10
If you are starting Beryl on login I'd remove it from the .config/autostart folder and try again.  Worse case scenario is that if Beryl isn't causing it all you have to do is put it back.  

That may not solve the issue, but it could remove the symptom.

---

### Post by taurus on 2007-04-10
> **cosmo18 said:**
> it says 
```
Filesystem                   Size     Used     Avail     Use%     Mounted on
**/dev/hdc3                     2.9G     2.9G      0            100%     /**
varrun                           363M    16k        363M        1%     /var/run
varlock                          363M        0        363M         0%    /var/lock
procbususb                    10M     88K         10M        1%    /proc/bus/usb
udev                                10M     88K          10M        1%    /dev
devshm                        363M         0        363M         0%   /dev/shm
lrm                                 363M    18M       346M        5%    /lib/modules/2.6.17-11-generic/volatile
/dev/hdc2                      7.7G   129M        7.2G         2%   /media/hdc1
```

The problem is that you are running out of disk space.  I believe Gnome would take around 2.5GB so since you only have like 3GB of harddrive, there is no room left.  Therefore, boot into recovery mode from GRUB menu again and do a little house cleaning, removing the archives.

```
aptitude clean
```
That would create some space.  Reboot and see if you can log back in again this time.

```
shutdown -r now
```

---

### Post by cosmo18 on 2007-04-10
I tried what you suggested but it gives me an error about being out of memory. I thought I had set the partitions up right but I guess not, I thought I set ubuntu to have 10gig of space, is there any way in the command line to reset the partition to a larger size? I thought I had set that 3gig for the swap file not the main program

PS oh and AkiraXXX I am not running beryl on this laptop, so I know thats not the problem

---

### Post by cosmo18 on 2007-04-10
on a lark I decided to try the command again and it let me log in, now to try and change the partition size without hosing everything

---

### Post by taurus on 2007-04-10
If you want to resize your partitions, you need to do that, using gparted, from the LiveCD since you can't resize partitions while you are using them.

---

### Post by cosmo18 on 2007-04-10
thanks for all the help

---

