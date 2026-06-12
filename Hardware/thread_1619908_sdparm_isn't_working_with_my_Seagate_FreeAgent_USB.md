---
title: "sdparm isn't working with my Seagate FreeAgent USB hard drive"
date: 2010-11-12
forum: Hardware
---

### Post by ptantiku on 2010-11-12
hi all,

  I have been using Seagate FreeAgent 2TB for few months now. And it's really annoying having it pop-up nautilus window everytime it spins down.
  I also did search on some work around. I found many of them using sdparm, but when I tried, it didn't work for me. 

This is what i got.
```
ptantiku@ptantiku-desktop:~$ sudo sdparm -a /dev/sdb
[sudo] password for ptantiku: 
    /dev/sdb: Seagate   FA GoFlex Desk    0155
Power condition mode page:
>>> warning: mode page seems malformed
   The page number field should be 0x1a, but is 0x00; try '--flexible'
```

first, the malformed mode page, which I figured that it needs  "-6" to tell which mode the drive is using. finally, I managed to see the configurations. 

But the problem comes when I tried to save it. it doesn't work.
```
ptantiku@ptantiku-desktop:~$ sudo sdparm -6 --clear STANDBY --save /dev/sdb
    /dev/sdb: Seagate   FA GoFlex Desk    0155
change_mode_page: mode page indicates it is not savable but
    '--save' option given (try without it)
```

Even I tried separate the command into 
sudo sdparm -6 --clear STANDBY /dev/sdb
sudo sdparm -6 --save /dev/sdb

the config still isn't saved.
```
ptantiku@ptantiku-desktop:~$ sudo sdparm -a -6 /dev/sdb
    /dev/sdb: Seagate   FA GoFlex Desk    0155
Power condition mode page:
  IDLE        0  [cha: n, def:  0, sav:  0]
  STANDBY     0  [cha: y, def:  1, sav:  1]
  ICT         0  [cha: n, def:  0, sav:  0]
  SCT       4294967286  [cha: y, def:9000, sav:9000]

```

"def" still equals 1, as same as "sav".

anyone know how to make it works?

---

### Post by SteveONCSU on 2010-12-29
I'm having the same problem, anybody found a solution?

---

### Post by philyoung316 on 2011-01-09
I'm also having this problem. I think the issue is the following:

change_mode_page:** mode page indicates it is not savable but**
    '--save' option given (try without it)

I've tried "set=STANDBY=0" and still no change. I think in the end the answer will be to install the goflex software from seagate in windows and disabling it there.

---

### Post by ptantiku on 2011-01-10
I think so, it seems the configurations won't be saved using hdparm tool, but it should do with Seagate software.

I'm currently pursuing this method 
[http://forums.seagate.com/t5/GoFlex-GoFlex-Desk-GoFlex-Pro/Auto-play-pop-up-amp-hard-drive-spins-after-shut-down/td-p/81670](http://forums.seagate.com/t5/GoFlex-GoFlex-Desk-GoFlex-Pro/Auto-play-pop-up-amp-hard-drive-spins-after-shut-down/td-p/81670)

which involves chatting with Seagate technician in order to get certificate for downloading Seagate Dashboard Utilities (224.8MB)

I'll post again if it does solve the problem.

---

### Post by ptantiku on 2011-01-11
Well, it's been working well so far. I'm marking this problem solved.

---

