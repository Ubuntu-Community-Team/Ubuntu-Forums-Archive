---
title: "&quot;Disk is being used outside design parameters.&quot;"
date: 2009-11-07
forum: Hardware
---

### Post by wizzim on 2009-11-07
I just installed Ubuntu Netbook Remix 9.10 for my Dell Mini 9. I keep getting the message that one or more disks are failing. Then i get the messange
DISK IS BEING USED OUTSIDE DESIGN PARAMETERS

So i checked around, reset bios, unchecked "spin down hard disk when possible" but it still is there. I am not the only one with this problem. Is this just a bug or do i need to do something about this?

---

### Post by wnderinguy34 on 2009-11-07
seems its not unusual [http://ubuntuforums.org/showthread.php?t=1307878](http://ubuntuforums.org/showthread.php?t=1307878) still doesn't mean its a good thing.I'm sure you found the same threads as I did and since a lot were using Karmic before it went gold,I'm surprised nobody has come up with a solution or posted an update either good or bad.

---

### Post by wizzim on 2009-11-07
so far i havent had any problems, just the error comes up

---

### Post by K.lundquist on 2009-11-09
I'm having this exact same problem on my Asus EeePC 701.  I did a completely fresh install from a USB thumb drive, wiping out WinXP.  I had zero issues or hiccups with the install.  A few hours later the "fail disk" message popped up.  So far there haven't been any other indications of a problem.

Netbook Remix is awesome... my EeePC is finally usable!  I just hope I'm not about to lose my SSHDD.

---

### Post by BandD on 2009-11-12
Same message for me on an eee 701 with 9.10 NBR.  But I can't notice any obvious failings and it seems only to appear after a resume from suspend.  If I restart it goes away.  

Super pleased with the new netbook remix, though.  The Devs made some very smart choices!  IMHO.

---

### Post by wizzim on 2009-11-14
Still saying it, but no problems... perhaps a bug.

---

### Post by Filkfive on 2009-11-28
I have the same thing too.  I am also using a Ubuntu Netbook Remix 9.10 for my Dell Mini 9, same as wizzim.

There is the option of clicking the box that says "Don't warn me if the disk is failing", but I'm hesitant to do that yet.

---

### Post by Manyette on 2009-11-28
HI All,  There have been many posts which have indicated that the built-in SMART technology in Karmic is a bit overly sensitive.  If you have a relatively new drive, it may be that it's just too sensitive, on the other hand, if it's an older drive, I think a good backup is in order.

---

### Post by Mr.Auer on 2009-12-15
Same here - Ive got an Eee 701 and I just resumed after suspend for the first time after installing Karmic on this machine - and after resuming, the very same error message popped up. No troubles either before or since, and the very first time I get this message. It would indeed seem to be a suspension / resume related bug...At least I hope so ;)

---

### Post by RMOP on 2009-12-31
Similar issue here with one notable difference: I installed 9.10 to a Class 6 SDHD SD Card and wiped my internal 4gb ATA drive on my eeePC 701. I did ENCRYPT the internal drive, but don't mount it. There are no data on it. I get the same error message. If I run the disk check, all looks OK. Sometimes the disk status then changes to healthy, sometimes not. Mine also seems to be related to resume from suspend, but not always.

---

### Post by OlorinIWas on 2010-01-04
Having the same message and spin up issue. I also suspect that two of my partitions have lost/written out about 250 GB combined...not happy about this one...has anyone lost available space?

---

### Post by hughv on 2010-01-15
Same for me on my Mini 9. Only at boot.
I Didn't get it 'til I switched to the latest Netbook Remix. I'm tempted to just turn off the warning.

---

### Post by kurth on 2010-01-23
I solved this issue on a eee701 by turning off swap and turning off atime.  Both swap adjusting file metadata will cause the SSD to wear and possibly fail.  Follow these instructions to disable swap and atime.

[https://help.ubuntu.com/community/EeePC/Using#Reducing Drive Writes](https://help.ubuntu.com/community/EeePC/Using#Reducing Drive Writes)

YMMV.

---

### Post by jwl1900 on 2010-03-18
A computer I'm fixing is giving me the same message.... Its a Dell mini9.  So far it hasn't broken down but it keeps giving me the message.  I had Ubuntu 9.4 on it and then Netbook Remix 9.10(which is when the problem occured), now Ubuntu 9.10. So far so good but I'm still getting the message.

---

### Post by mshenrick on 2010-09-25
> **K.lundquist said:**
> I'm having this exact same problem on my Asus EeePC 701.  I did a completely fresh install from a USB thumb drive, wiping out WinXP.  I had zero issues or hiccups with the install.  A few hours later the "fail disk" message popped up.  So far there haven't been any other indications of a problem.

Netbook Remix is awesome... my EeePC is finally usable!  I just hope I'm not about to lose my SSHDD.

exactly what he said ^

---

### Post by doctor_regtools on 2011-01-04
Just started getting this problem on a fresh install of UNR 10.10 on my eee 701.  I was previously on easy peasy (based on 8.04 I believe) which didn't report the issue.

Should I just turn off the warning, apply Kurth's suggestion, or what?

Thanks for any recommendations

---

### Post by mshenrick on 2011-01-04
> **doctor_regtools said:**
> Just started getting this problem on a fresh install of UNR 10.10 on my eee 701.  I was previously on easy peasy (based on 8.04 I believe) which didn't report the issue.

Should I just turn off the warning, apply Kurth's suggestion, or what?

Thanks for any recommendations

ive just ignored it, and it hasnt died so far!

---

