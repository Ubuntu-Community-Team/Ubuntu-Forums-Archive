---
title: "Post base install: freezes at 44%"
date: 2006-02-03
forum: Installation &amp; Upgrades
---

### Post by codebang7788 on 2006-02-03
This is my 10th time installing on my Toshiba Satellite m40/m45 laptop.

I've md5sum my iso, correct.

The base installation went fine. After the reboot the install hangs at 44%...
The error message says that my package is not installed correctly, I should try reinstalling....

Reboot, kdm starts. Login... Then exception panel pops up... and the system hangs...

I'm trying the server install thing right now...

Also I've done the CD check in expert mode and it tells me that I have a bad package...But I've burned 5 disks now at decreasing speeds (last one burned at 4x)... None of them worked so far...


Help.

BTW SUSE 9.3 installs fine btw but I want to try something else...Also note that my SUSE disks have problems too. I can do the default KDE install fine but when I tried to install with some other packages like SVN the install also crashes with bad pacakge errors... I got these disks from a friend...

---

### Post by codebang7788 on 2006-02-03
Okay an update on server installation.

After installing the server.

I did sudo apt-get install ubuntu-desktop
THis goes all the way up to 99% or so and give me an
error about unable to fetch some package, MD5SUM incorrect...

Could it be my cd-drive??? Perhaps my drive is having problems with stuff near the end of disk? 

I'm doing apt-get install gdm just to see what will happen.

---

### Post by codebang7788 on 2006-02-03
Haha it worked on a new install! (server install didn't work)

I think the problem is that I tried with the noapic nolapic options before but I had a bad disk then...Subsequent reinstalls I forgot to input those options.

ON my last install I remembered to use those options and everything worked!

Or it could just be something screwy with my disk/disk drive...

Thank the linux gods...

---

