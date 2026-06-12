---
title: "Unable to mount Location"
date: 2009-11-05
forum: Hardware
---

### Post by joelmcw on 2009-11-05
Hello. I'm using an external USB HDD, Seagate Barracuda 7200.7
ST380011A with my laptop.

Today when i tried to open the it up to look at my photo's I get this message...

"UNABLE TO MOUNT LOCATION". "cannot mount file"

Now, I'm a noob when it comes to things like this so im sorry in advance for my lack of understanding, i'm new to ubantu too so I feel totally lost. I tried to look on other threads about this but could not seem to find much help, or it was just over my head and didn't understand

Any help is much appreciated, please let me know if you need any further information to assist, thanks in advance.
> johnmc@johnmc-laptop:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1            152357444  10137724 134480408   8% /
varrun                  257132       104    257028   1% /var/run
varlock                 257132         0    257132   0% /var/lock
udev                    257132        56    257076   1% /dev
devshm                  257132        24    257108   1% /dev/shm
lrm                     257132     40000    217132  16% /lib/modules/2.6.24-25-generic/volatile
johnmc@johnmc-laptop:~$ 

---

### Post by joelmcw on 2009-11-07
bump, any help would be nice thanks =p

---

### Post by beacon on 2009-11-09
My problem is not quite the same, but almost. I get the same message when I insert certain DVDs. Others work well. I have read the threads in other posts and tried out various options, When I typed in one suggested command (mount /media/cdrom)), I got the following message: 

mount: wrong fs type, bad option, bad superblock on /dev/sr0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

I can't make much sense of it, so what should I do next? As I say some DVDs work and others do not. (I believe these are blank but was trying to check.)

---

