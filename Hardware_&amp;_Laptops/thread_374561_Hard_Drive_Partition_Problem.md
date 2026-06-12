---
title: "Hard Drive Partition Problem"
date: 2007-03-02
forum: Hardware &amp; Laptops
---

### Post by Prometheus.172214 on 2007-03-02
Allright. Call it a nasty hangover from Windows or sheer dumbness on my part, but this is what I did. When I started the Ubuntu Installation (Edgy Eft), I divided my 40Gb hard drive into three partitions. The first was a 6Gb Partition (Ext3) into which I installed Ubuntu and this is /hda1. The second is a 31Gb (Ext3) and errr . . . also a primary partition instead of being extended which is /hda2. The last which is the rest of the space of about 1Gb is the Swap partition which is /hda3. At this point, I am sure anyone reading this will probably give me that knowing smirk that I am a fool, because the /hda2 is no where seen. Question: Is there a way I can get the 31Gb into use? I have a program called qparted (Forgive me if the name is wrong, I am posting in from work and used the program only once) and all I managed with it was to format /hda2 (31Gb) and that was about it . . . All I am trying to do is avoid reinstallaing the O.S. and get to using the 31Gb. (I am being paid to reinstall Windows a thousand times in a year and am really hoping and am sure Linux has a better way to handle this)

---

### Post by kidders on 2007-03-02
> **Prometheus.172214 said:**
> Allright. Call it a nasty hangover from Windows or sheer dumbness on my part, but this is what I did. When I started the Ubuntu Installation (Edgy Eft), I divided my 40Gb hard drive into three partitions. The first was a 6Gb Partition (Ext3) into which I installed Ubuntu and this is /hda1. The second is a 31Gb (Ext3) and errr . . . also a primary partition instead of being extended which is /hda2.That seems sensible ... nothing wrong so far. :-)

> **Prometheus.172214 said:**
> The last which is the rest of the space of about 1Gb is the Swap partition which is /hda3. At this point, I am sure anyone reading this will probably give me that knowing smirk that I am a fool, because the /hda2 is no where seen.Does that mean **ls /dev/hda2** returns "ls: /dev/hda2: No such file or directory"?

---

### Post by Prometheus.172214 on 2007-03-02
Yes. it does ........ :(  ls /dev/hda2 returns "ls: /dev/hda2: No such file or directory"?

Lost is a good word for me here ...... (17 years on DOS and Windows can do some brain damage)

---

### Post by kidders on 2007-03-02
> **Prometheus.172214 said:**
> Yes. it does ........ :(  ls /dev/hda2 returns "ls: /dev/hda2: No such file or directory"?Eek... perhaps you've accidentally deleted it. Does **sudo fdisk -l /dev/hda** also indicate that it's missing? (Could you post the output?)

> **Prometheus.172214 said:**
> 17 years on DOS and Windows can do some brain damage)Well done for lasting that long! Hehe.

**Edit:** Just in case it makes any difference, it's always a good idea to reboot after repartitioning the drive with a running Linux system partition on it **before** formatting things, or doing other stuff.

---

### Post by Prometheus.172214 on 2007-03-02
Ouch ! I am currently not at the system, but at work . . . . I'll have to try this the first thing I get home. I am also trying to the wireless to work on this notebook and am currently in the solution not found status with that also. Well, this is the first time I have tried Linux, I like the way it works ... lesser junk and more work done. I'll let you know the first thing I am back home and check. Maybe I over looked something during the first attempt. 

(Lasting long in Windows was not out of choice but because I had no other choice. My office I.T. had not given us a VPN client for Linux and now that we have one, it works way better than anything else I have seen. 2 decades ago as a kid, I watched my Dad work on a Unix box and went like Woah ! Now, I start with Linux and say Yeah ! and Woah ! This is sweet).

---

### Post by kidders on 2007-03-02
> **Prometheus.172214 said:**
> Well, this is the first time I have tried Linux, I like the way it works ... lesser junk and more work done.Hopefully you and Linux will *continue* to get along! :-)

Incidentally, just in case I need to start thinking about recovery scenarios, do you need to get any of the data on this wandering disk partition back?

---

### Post by Prometheus.172214 on 2007-03-02
Data loss is no problem. I just setup this notebook pc and am in the learning and enlightenment phase at the moment. However, I was just hoping to find a solution so if there is a problem like this later, I would like to find out how not to mess things up. I'll give you the details of the output a.s.a.p. Like I said I am still at my desk and have a pile of work (well who does'nt) ....

---

### Post by kidders on 2007-03-02
No rush! It's *your* thread.

---

### Post by Prometheus.172214 on 2007-03-03
Phew ! It works now. 

First, before you read further, you might want to take a deep breath and be seated because I am sure you will start laughing the moment I tell you what the problem is. 


Dumb me ..... I forgot there was something called mounting that I had to do.
I made a mount point. Mounted the new filesystem. Finally I made an entry describing the new filesystem so it would be mounted automatically mounted at boot time......

Darn, this is embarassing !

---

### Post by kidders on 2007-03-03
Hehe. Glad it's working. I'm confused though... didn't you say /dev/hda2 didn't exist? If so, what are you mounting?

---

### Post by Prometheus.172214 on 2007-03-04
Well, for starters I checked in all the wrong places. Then, when you suggested the 2 commands, it got me thinking of 2 things. One, during the installation, the /hda1 (Main parition) and the /hda3 (Swap) are formatted and initialized, but the /hda2 is untouched. So I had to locate it and format it and then set mounting rules. I feel like a freshman in his first class.... I guess I just jumped to conclussions before trying anything at all.

---

### Post by kidders on 2007-03-04
> **Prometheus.172214 said:**
> I feel like a freshman in his first class.... I guess I just jumped to conclussions before trying anything at all.Hehe. That's kewl... I just wanted to be sure there was nothing funny going on. :-)

---

