---
title: "I know the problem but I don't know how to fix it"
date: 2009-01-21
forum: Hardware
---

### Post by Sinning_Sinner on 2009-01-21
O.K. so a couple of days ago I got the Error 16 message on bootup. I left the computer alone for a while and tried again. This time I did not get the error 16 message on bootup but instead a repeating list of errors. Well I finally got it to at least get to the login screen but after entering the required information I got an error that said the HD was full and could not write to the drive and hence would not boot the GDM until the error was fixed.

So my question is how can I format the hard drive or at least be able to delete some info off it so it will boot? I tried making a new live CD but there are no formating options on there.

Please help.

---

### Post by tommcd on 2009-01-22
If you can't boot Ubuntu then bootup the Ubuntu live CD and run: **sudo du -csh /***. This may take a minute to run. It will print out a list of each directory along with the size of each directory. If you then find, for example, that /tmp or /var are very large you can focus on them by running **sudo du -csh /var/***, etc. You can then mount your root partition and delete stuff to free up space. Anything in /tmp or /var/tmp can be safely removed. Also, check the trash directories:
[http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)

EDIT: Before booting from the live CD see if you can boot to recovery mode. You can then run **du -csh /*** and find out where all the space went so you can delete stuf to free up space. Also run:
> apt-get clean

---

### Post by y@w on 2009-01-22
> **tommcd said:**
> If you can't boot Ubuntu then bootup the Ubuntu live CD and run: **sudo du -csh /***. This may take a minute to run. It will print out a list of each directory along with the size of each directory. If you then find, for example, that /tmp or /var are very large you can focus on them by running **sudo du -csh /var/***, etc. You can then mount your root partition and delete stuff to free up space. Anything in /tmp or /var/tmp can be safely removed. Also, check the trash directories:
[http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)

If you customized the partitioning when you installed, it might just be that one of them is full (by default it's one big partition if you select the "use entire disk" method). If that's the case, a df -h will show you exactly which partition is full and may let you narrow it down faster.

---

### Post by Sinning_Sinner on 2009-01-22
I can not even get the live cd to boot up.

---

### Post by tommcd on 2009-01-23
> **Sinning_Sinner said:**
> I can not even get the live cd to boot up.

Problems with the hard drive should not effect your ability to boot a live CD. If you can't even boot a live CD then something else must be wrong.

---

