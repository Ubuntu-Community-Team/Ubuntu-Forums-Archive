---
title: "batterylife-extending fix causes excessive ammount of messages in syslog"
date: 2008-05-20
forum: Hardware
---

### Post by miga on 2008-05-20
hi, I'm using a fix to not charge my thinkpad battery over a certain %, and to start charging again at a certain %  --> [http://ubuntuforums.org/showthread.php?t=546537](http://ubuntuforums.org/showthread.php?t=546537)

my problem with this way, is that I get a repeated message invoked from power.sh while connected to AC, this does not appear when running solely on battery power.

giving me

[17539.965688] smapi smapi: set_real_thresh: set stop to 95 for bat=0
[17540.190538] smapi smapi: set_real_thresh: set start to 59 for bat=0
in systemlog (dmesg entries)
every 5 or so seconds.. 

Is that a normal function? if not, how do I reduce the ammount of checks done, or just how to reduce the ammount of messages showing up in syslog.. oh, and the charging of my battery is superslow while powered up and being used, but I guess that's how it is (brand new laptop, never tested in windows, tp R61i, nor did I test it without the fix) Recharging done when powered off is fast, however..

---

### Post by miga on 2008-05-23
shameless bump, I'm kind of inclined not to use my laptop before I figure out this bit :) or just removing the battery when on AC =P

---

### Post by sdennie on 2008-05-23
> **miga said:**
> shameless bump, I'm kind of inclined not to use my laptop before I figure out this bit :) or just removing the battery when on AC =P

You'll have to charge the battery sometime.  ;)

I don't use that particular tip but, one thing you could try would be to see if the tp_smapi kernel module has a flag that reduces the syslog spam.  Something like this should get you moving in the right direction:

```

modinfo tp_smapi

```

Check the bottom parts of the output.

---

