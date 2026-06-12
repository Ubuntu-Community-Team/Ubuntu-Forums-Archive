---
title: "need to disable seagate external HD sleep / auto spin down usind sdparm"
date: 2008-04-03
forum: Hardware &amp; Laptops
---

### Post by Tgon on 2008-04-03
I have a seagate 500Gb external HD, its ntfs so I had some initial problems getting it to mount and be rw.  But now it works, the only problem I still have is that it auto spins down, or goes to sleep, after several minutes of inactivity.

I've looked around for fixes and found this:
[http://www.cgkreality.com/2007/11/27/seagate-freeagent-idle-under-linux/](http://www.cgkreality.com/2007/11/27/seagate-freeagent-idle-under-linux/)

I basically get this far

[B]1. installed sdparm
2. I know my HD is /dev/sdc1
3. entering "sudo sdparm -a /dev/sdc1" returns[/B]
    /dev/sdc1: Seagate   FreeAgentDesktop  100D
Power condition mode page:
  IDLE        0  [cha: n, def:  0, sav:  0]
  STANDBY     1  [cha: y, def:  1, sav:  1]
  ICT         0  [cha: n, def:  0, sav:  0]
  SCT       9000  [cha: y, def:9000, sav:9000]
**4. entering "sudo sdparm –clear STANDBY -6 /dev/sdc1" returns**
Unexpected extra argument: /dev/sdc1

if anyone can see what i'm doing wrong i'd be glad to know {:0)

---

### Post by Tgon on 2008-04-03
Think I found a fix already,

[http://alienghic.livejournal.com/382903.html](http://alienghic.livejournal.com/382903.html)

basically the drive wasn't started heres how to do it if anyone else has this problem:

[B]1. install sdparm
2. find location (e.g.  /dev/sdc1)
3. enter "sudo sdparm -a /dev/sdc1"
4. enter "sudo sdparm --command=start /dev/sdc1"
5. enter "sudo sdparm --clear STANDBY -6 /dev/sdc1"[/B]

then do **"sudo sdparm -a /dev/sdc1"** to check its done.  I've heard this fix might only work until you restart but I've also heard that it is a perm fix.  I'll let you know once I test it further.

---

### Post by Tgon on 2008-04-03
seems to be ok {:0)

---

