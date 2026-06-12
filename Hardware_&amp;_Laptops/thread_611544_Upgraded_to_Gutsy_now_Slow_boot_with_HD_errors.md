---
title: "Upgraded to Gutsy now Slow boot with HD errors"
date: 2007-11-13
forum: Hardware &amp; Laptops
---

### Post by swedishlf on 2007-11-13
Just updating the wife's laptop to from Feisty to Gutsy.  It's an older machine ca. 1997, but it ran feisty very well.  We noticed the boot took quite a bit longer with gutsy and I did some sleuthing.  Upon boot, at about 6 seconds it hangs.  Then at 38 seconds or so it spits out the following:

ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
ata1.00: cmd c8/00:08:00:00:00/00:00:00:00/00 tag 0 ldb 0x0 data 4096 in

this repeats 4 times at roughly 30 second intervals.  After the 4th time, the computer proceeds to boot normally.

I ran 

sudo smartctl -a /dev/sda

and it mentions that Load_Cycle_Count is "FAILING_NOW" and it's just shy of 600000 which seems a bit high.  I did not run this command before updating to Gutsy though so I have no idea if this is a symptom, cause, or just coincidence.

Does anyone have any advice?  It would be most appreciated!

The laptop:
1Ghz Intel Celeron
512 MB RAM
30 GB Toshiba MK3017GAP HD
if more info is needed please, let me know!

Thanks all.

---

### Post by swedishlf on 2007-11-14
Bump, no luck so far.

---

### Post by Daelyn on 2007-11-14
There is a "BUG" (not really a bug, but reported as one) that has caused some issues with harddrives for ALOT of people since upgrading to Gutsy.

Ta en titt på följande forum tråd (sorry guys, just had to use some swedish):
[http://ubuntuforums.org/showthread.php?t=591503](http://ubuntuforums.org/showthread.php?t=591503)
You will find alot of commands and stuff in there that could help sort the issue.

Maybe it could be that your old lappie HDD does not have support for these SMART/hdparm commands and that is causing a conflict with the new gutsy.

Also, 600k load/unload cycles is high. It is about there that the HDD manufacturers specify potential fail point. It could last for hundreds of thousands more, but, who knows.

Try disabling the features
```
 sudo hdparm -B255 /dev/hda 
``` replace the "hda" with the correct device in case of other.

Hope it helps and hope that the HDD isn't on the verge of dying on ya.

PS. Snöa inte in nu där hemma i Svenne land ;P

---

### Post by ubuntu_demon on 2007-11-21
If you are seeing things like :
> 
ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
ata1.00: cmd c8/00:08:00:00:00/00:00:00:00/00 tag 0 ldb 0x0 data 4096 in


**You should backup all your data now.** You should use the tool your harddisk manufacturer recommends to diagnose your disk (probably included on ultimate boot cd-rom). Follow the instructions of this tool and it's documentation. (it might be the case that you can repair a few bad sectors by writing zero's to them or that you can do a low level format). If you keep seeing errors like this or your diagnostic tool says your harddisk isn't healthy anymore **you probably need to go shopping for a new harddrive.**

The correct value to disable apm is 254 instead of 255. 

Everyone please read the first post of the Load_Cycle_Count support thread :
[http://ubuntuforums.org/showpost.php?p=3733762&postcount=1](http://ubuntuforums.org/showpost.php?p=3733762&postcount=1)

---

