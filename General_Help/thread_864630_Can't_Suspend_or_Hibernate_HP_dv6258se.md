---
title: "Can't Suspend or Hibernate HP dv6258se"
date: 2008-07-19
forum: General Help
---

### Post by ttwaro on 2008-07-19
Help! I have been running Kubuntu and/or Ubuntu since 6.04 and running them on my HP dv6258se since 7.04. With this laptop I have never been able to successfully suspend or hibernate with (k)ubuntu. I was sure hoping 8.04 was going to change this for me but unfortunately, no.

Whenever I attempt to suspend or hibernate I have some disk activitiy followed by a black screen with a flashing cursor in the upper left corner. I have to hold the power button down to finally power off the laptop. I have read and tried everything I can find to no avail. I have even resorted to reinstalling many times just to make sure that I am at a common starting point. Still no dice. I read where others have had success with some dv6xxx laptops but not me.

My specs are:
[INDENT]OS: Ubuntu 8.04 (32-bit)
CPU: AMD Turion(tm) 64 X2 Mobile Technology TL-56
Memory: 2GB
Swap Partition: 4GB
Video: nVidia (driver version 169.12
Boot: kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=7e3c8786-69a9-4d6a-b2bf-ebaa4626a0ea ro quiet splash
[/INDENT]

Does anyone have any ideas of how to get suspend/hibernate working on this thing. This is the only thing left that I really would like to have working. (It is embarrassing to show off Ubuntu in front of Windows users only to have it lock dead when suspending.) If you need any other information to help solve this just ask. I just don't know what else to do.

Tom

---

### Post by ttwaro on 2008-07-20
Something changed. Suspend just worked for me for the very first time. It even restarted my wireless connection again. I don't know what changed for the better. I did start up Compiz to play with but I really expected that to make things worse instead of better. Next I need to try Hibernate.

---

### Post by ttwaro on 2008-07-20
I got overly excited. I successfully suspended and came out twice but three times is not a charm. I just tried to show someone that it works but it didn't. I now just get a black screen, no cursor, when trying to suspend. I also tried to hibernate after I rebooted. This also failed with the black screen and no cursor.

Still looking for ideas though I must be getting close since I have proved that this will suspend sometimes. I know, I'm picky but I really want it to work ALL the time and of course to also have hibernate working ALL the time ;-). I have updated my original post with some additional information.

Thx

---

### Post by ttwaro on 2008-07-20
I finally think I solved this problem. I followed the information at [Sean's Blog]("http://blog.vaxius.net/?p=43") and now both suspend and hibernate have successfully worked several times for me.

If there are any developers reading this I suggest they take a look at Sean's Blog above, especially the section titled 'It works! Well, it kind of works…'. The script has made it worked every single time so far.

I hope this will help others to solve this very perplexing issue. Now I can gloat again to my Windows buddies.

:)

---

### Post by ttwaro on 2008-07-20
I spoke too soon. After my last successful startup from hibernation I did a suspend and once again hung on the black screen with flashing cursor. Darn. So maybe it is just hibernate not working completely. We will see.

---

### Post by ttwaro on 2008-07-21
This morning I have tried clicking Log off button -> Suspend four times. The first three times it froze during suspend with the black screen and flashing cursor. The fourth time it suspended successfully and resumed successfully. I would really like some help in debugging this. There must be a "secret" incantation that I can say to make this work reliably. Help!

---

### Post by seedyburner on 2008-07-21
Hey Tom, 

Just thought I'd let you know that I feel your pain. I have the exact same setup except for mine has a *Minty* flavor. I'm having a few other issues too but I need to do a little more digging. My main and most disappointing thing so far is the Nvidia driver all together. Definately let me know if you find anything out. I'll do the same.

---

### Post by ttwaro on 2008-07-24
**UPDATE:** I've just applied the Ubuntu update for kernel (2.6.24-20-generic) and the results for suspend and hibernate are the same. I sure wish someone with more knowledge than me would help me debug this. I have no idea what to look for or which logs to look at to try to solve this. I know there are a lot of others out there with similar hardware that have the same problem (though I know there are others without this problem).:confused:

I just don't have a clue what is causing the problem. Does it just get so far and wait? or freeze? is it HP? is it nVidia? is it Broadcom? is it Samba/CIFS? is it ______? (fill in the blank)

That's why I wish someone could/would tell me how to go about debugging this. The trial and error I have been using is very unscientific and is only producing errors.

Sorry seedyburner, no luck yet.

---

