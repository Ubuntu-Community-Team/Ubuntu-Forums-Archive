---
title: "Problem on Dual Booting  Windows XP and Ubuntu"
date: 2009-08-27
forum: Installation &amp; Upgrades
---

### Post by varunit on 2009-08-27
Hello Guys... I have a problem. 

First i installed windows followed by ubuntu 9.04
Everything is working fine and i am also able to dual boot.
Now for some reasons i have reinstalled XP hoping that i can still dual boot XP and Ubuntu.
But Now the entries for Ubuntu in MBR do not appear. Only Windows XP boots..

What happened to ubuntu?? I still have all the files and necessary pertiotions for ubuntu. I have not deleted anything yet??

Do i have delete those partitions and reinstall ubuntu

Can anyone help me with the situation???:confused:

Thank you in advance:)

---

### Post by KinKiac on 2009-08-27
I may be wrong as I am a bit of a noob, but it sounds to me like you may have to re-install Grub.  In doing so it should pick up any OS's you have, and allow you to boot to whatever.  Windows probably overwrote your MBR.

---

### Post by raymondh on 2009-08-27
> **varunit said:**
> Hello Guys... I have a problem. 

First i installed windows followed by ubuntu 9.04
Everything is working fine and i am also able to dual boot.
Now for some reasons i have reinstalled XP hoping that i can still dual boot XP and Ubuntu.
But Now the entries for Ubuntu in MBR do not appear. Only Windows XP boots..

What happened to ubuntu?? I still have all the files and necessary pertiotions for ubuntu. I have not deleted anything yet??

Do i have delete those partitions and reinstall ubuntu

Can anyone help me with the situation???:confused:

Thank you in advance:)

Did you (by accident) install/reformat over your ubuntu install?

Boot into the liveCD and access a terminal (applications > accessories) to type and post back output of:

```
sudo fdisk -l
```

small L, not I nor 1.

If ubuntu is still there, you may try to re-install GRUB because XP's install would've written over the MBR.  Here's a tutorial:

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

If Ubuntu is not there, time to re-install Ubuntu ;)

Do back up and defrag windows.  Even if it's a new installation, it  would'nt hurt to do so.

---

### Post by snakeman21 on 2009-08-27
Windows does not acknowledge the possibility of dual booting.  It assumes that it will be the only OS, so that's the only option it gives you.  Most likely, it overwrote your MBR.  You will need to reinstall GRUB.  You better just hope Windows didn't overwrite your Ubuntu partition!

---

### Post by KinKiac on 2009-08-28
> **snakeman21 said:**
> Windows does not acknowledge the possibility of dual booting.  It assumes that it will be the only OS, so that's the only option it gives you.  Most likely, it overwrote your MBR.  You will need to reinstall GRUB.  You better just hope Windows didn't overwrite your Ubuntu partition!

This is why I give windows its own 80gig HDD, if it wont play nice then ill lock it up in its own little playpen, lol.

---

