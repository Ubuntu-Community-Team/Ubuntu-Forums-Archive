---
title: "Xorg changes make Ubuntu unuseable"
date: 2009-05-03
forum: Installation &amp; Upgrades
---

### Post by Canuck.old on 2009-05-03
A week ago I had a nicely running 8.04 Hardy system, but
the system disk died. As a paranoid old software type my
backups are (barely) good enough but neither a new copy
of 8.04 or the new 9.04 work after some xorg changes.

In both cases a new install works, for a while at
1856x1392. a number that cannot be changed using any of the
tools I can find. But this does not remain the problem.
After a reboot or two - perhaps 3 the best resolution
changes to 800x600. Both of these values are completely
useless! 1856x1392 is way to small for my eyes. However at
least NetBeans is usable for a few minutes of eye strain.
800x600 is totally useless. There is not enough on the
screen to make programming practical.

I have played with xorg.conf on both systems but there is
not enough stuff around to modify. (I have not played with X
in many years). I did a backup & I KNOW the xorg.conf file 
remained unchanged through this metamorphosis.

How can I get a working system back? Windows is not
an option. Perhaps I have to go to solaris. I used it in the
90's but I want linux for several reasons.  I am sure you all
understand this well.

Where is the solution? Help me please!

Thank you for your time.

dkr

PS
My system has a Gforce 6600LE video card but I am not sure
why it matters, but it seems that not everyone is having this
problem.

---

### Post by Jabz.biz on 2009-05-03
Hmm, isn't the xorg.conf file empty on default? Mine is completely empty since 8.04. 

I always found help at system > Screenresolution. Seems to work without the xorg.conf

Good luck. I will update next week...hope it will be a smooth process.

---

### Post by Canuck.old on 2009-05-03
> **Jabz.biz said:**
> Hmm, isn't the xorg.conf file empty on default? Mine is completely empty since 8.04. 

I always found help at system > Screenresolution. Seems to work without the xorg.conf

Good luck. I will update next week...hope it will be a smooth process.

system>Screenresolution will not change anything (FYI I usually use
KDE but I will try anything).
Not empty but just a bare outline. I'll try removing this & see!
Thanks for you effort.
dkr

---

### Post by Canuck.old on 2009-05-03
> **Canuck.old said:**
> A week ago I had a nicely running 8.04 Hardy system, but
the system disk died. As a paranoid old software type my
backups are (barely) good enough but neither a new copy
of 8.04 or the new 9.04 work after some xorg changes.

In both cases a new install works, for a while at
1856x1392. a number that cannot be changed using any of the
tools I can find. But this does not remain the problem.
After a reboot or two - perhaps 3 the best resolution
changes to 800x600. Both of these values are completely
useless! 1856x1392 is way to small for my eyes. However at
least NetBeans is usable for a few minutes of eye strain.
800x600 is totally useless. There is not enough on the
screen to make programming practical.

I have played with xorg.conf on both systems but there is
not enough stuff around to modify. (I have not played with X
in many years). I did a backup & I KNOW the xorg.conf file 
remained unchanged through this metamorphosis.

How can I get a working system back? Windows is not
an option. Perhaps I have to go to solaris. I used it in the
90's but I want linux for several reasons.  I am sure you all
understand this well.

Where is the solution? Help me please!

Thank you for your time.

dkr

PS
My system has a Gforce 6600LE video card but I am not sure
why it matters, but it seems that not everyone is having this
problem.

OK I tried removing xorg.conf and as a result gnome-display-properties
gives me the following options:
800x600
640x480
400x300
320x240
which are all less than wonderful.
I did not actually try any of them.

---

### Post by Jabz.biz on 2009-05-03
Have you tried adding your preferred resolution to xorg.conf? 

Maybe this helps. 
[http://ubuntuforums.org/showthread.php?t=48195](http://ubuntuforums.org/showthread.php?t=48195)

BTW: What graphics card do you use?

---

### Post by Canuck.old on 2009-05-03
> **Jabz.biz said:**
> Have you tried adding your preferred resolution to xorg.conf? 

    That reference is a start - but the outline xorg.conf is so
    lacking in
    content that it is to easy to screw up. (I have had to resort to
    Knoppix to recover once already) Is there a more complete example
    somewhere I can look at?

snip

BTW: What graphics card do you use?

Gforce 6600 LE

thanks again
dkr

---

### Post by Canuck.old on 2009-05-03
> **Jabz.biz said:**
> Hmm, isn't the xorg.conf file empty on default? Mine is completely empty since 8.04. 

I always found help at system > Screenresolution. Seems to work without the xorg.conf

Good luck. I will update next week...hope it will be a smooth process.

system > Screenresolution at best offers the 800x600 resolution.
Even if that was ok in a bit / cm way 800x600 is 4x3 my relic
is 5x4 (my preference is 1280x1024)

---

### Post by Canuck.old on 2009-05-04
Will someone please post a copy of the xorg.conf file before
details were removed. It would be nice if the data was for
a Gforce card but anything would be a help.
Thank you.
dkr

---

### Post by Canuck.old on 2009-05-05
More stuff - I upgraded to linux 2.6.24-24-generic and upon reboot
the resolution went to 1856x1392. I did try to change this to 1280x1024 using gnome-display-properties but it did not seem to take. This morning when I restated the machine the resolution was 
back to 800x600. 
I checked and there is now no xorg.conf file. I deleted the
outline version that was there.
Thank you for your time.

---

### Post by Mark Phelps on 2009-05-05
Try "sudo displayconfig-gtk" and see if that helps.  Lets you choose different monitors with different resolution settings.

---

### Post by Canuck.old on 2009-05-05
Thank you Thank You THANK YOU!!

Next time please beat me with a stick - until I investigate all of the
applications parameters!
Thank you for your time.
dkr

---

### Post by Canuck.old on 2009-05-07
It appears that the real problem is:
A KVM interferes with the ability to detect monitors. I
have a kvm switch. So if this is indeed a problem; I
have it.

Thanks again for all of your help!
dkr
PS is is working fine now!

---

### Post by CBHedricks on 2009-05-07
I have had some KVM's work with Linux for about 6 months then 'poof' nothing.  Does not seem to matter what brand you put into the mix - they all are pretty much worthless POS's after about 6 to 8 months of use.

Windows / Linux does not make much of a difference with most of the IOGEAR units that I have been using.  Ones that I stay away from are Belkin (killed a DVI port on both monitor and computer), TrendNet (never lasts more than 6 months) and CablesToGo (dies in 3 months). 

Ones that I have found to be best bang for the buck:
[LIST]
[*]IOGear
[*]LinksKey
[*]Tripplite
[/LIST]

Hope that helps out.

CB

---

