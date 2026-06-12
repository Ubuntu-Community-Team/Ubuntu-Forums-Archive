---
title: "MY 4GB Flash Drive Thinks it's 21 MEGS!!!!"
date: 2008-08-25
forum: Hardware
---

### Post by cat5e_ on 2008-08-25
I was trying to put Ubuntu on my flash drive one time. I messed up, and gave up. It used to be 4GB, and the partition that I created cut about 750 megs out of it so it was about 3GB, and that was all that showed up on the computer. I tried formatting it back to the way it was, but it's all messed up now. I tried deleting partitions in Ubuntu, but didn't work very well. Then I went into Windows XP and did a format... brought it down to 21.2MB!

Can anyone explain to me how to restore it to the 4GB state using Windows XP or Ubuntu?

If I need to go into Terminal, please tell me exactly what to say, as I'm clueless. 

THANK YOU FOR ANY HELP!

---

### Post by shak541 on 2008-08-25
try to use gnomes partion editor... delete all partions(all data will be lost) then create 1 and format it to whatever u want :D

---

### Post by Lord Xeb on 2008-08-25
Go out, get GParted in the synaptic manager >_> and use that. Also, if that doesn't work, use this (WARNING, **ALL** INFORMATION WILL BE DESTROYED WITH THIS) while in root:

```
fdisk -l
```This will tell you all your drives and partitions and their sized etc... just look for the 4GB one

next type this:
```
 **shred [COLOR=#000099]-v[/COLOR][COLOR=#990000]f[/COLOR][COLOR=#000099]z[/COLOR] [COLOR=#990000]-n[/COLOR] 100 ****/dev/your drive**
```
or you could:
```
**shred [COLOR=#000099]-v[/COLOR][COLOR=#990000]f[/COLOR][COLOR=#000099]z[/COLOR] [COLOR=#990000]-n[/COLOR] 100 /media/your_drive**
```

Then just use gparted to reformat and repartition it out :D

---

### Post by cat5e_ on 2008-08-25
Thanks for that Terminal code. I'm using that right now. Seems to be working, but takes forever since my flash drive is REALLY slow (Sony memory...). There was nothing important on the drive that cannot be lost.

If this doesn't work, I'll try to find the partition thing you guys mentioned, just figured this would be faster since I don't care if files are lost... actually I want them deleted since I'll be selling this to a friend of mine, but there was never any personal information, so it's not like I need to overwrite the old data then erase again.

Thanks a lot for the help guys!

---

