---
title: "No swap usage...ever"
date: 2008-07-15
forum: General Help
---

### Post by Mr.Useless on 2008-07-15
My swap is NEVER in use, i will take a screenshot of my converting a video, using multithreading, that gets about 93% out of each core, and then also extracting 2 videos from seperate archives, (each of which use split archives) my ram goes up usually to around 45% max, but my SWAP is never used or to what i can see...anyone got an idea?

i also have firefox and amsn open and amarok...

well heres the SS

Could this be my screenlet not picking up my swap usage...or is it true....my swap PHails

[IMG]http://img26.picoodle.com/img/img26/4/7/15/f_badtimesm_18afd35.png[/IMG]

---

### Post by lisati on 2008-07-15
Unless your system seems to be running unacceptably slowly, I'd say its ability to get along without swapping might be a sign that you've got a good system!

---

### Post by kunixos on 2008-07-15
for starters, it doesn't look like your ram useage is high enough to 'switch' to the swap. aside from that, check your /etc/fstab file to make sure the swap partition is automatically loaded at boot time. if it's not in there do one of these:
```
swapon /dev/sda2
```
where '/dev/sda2' is the swap partition.

hope this helps!

---

### Post by Mr.Useless on 2008-07-15
that image is huge sorry

---

### Post by iaculallad on 2008-07-15
It's a good thing when the swap partition isn't being used, it mean your RAM installed is being used efficiently. Activated swap means you're system need more physical RAM to process application threads.
You wouldn't want to to use it anyway, since it's much slower than using true RAM.

---

### Post by Mr.Useless on 2008-07-15
[COLOR="Lime"]FSTAB[/COLOR]

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=119fbfc2-d517-4905-b50b-2a77e3b47a4e /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=ec349e45-2db2-4034-8f23-5bf806d17a0a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```

---

### Post by Mr.Useless on 2008-07-15
Ahh ok well if thats the case im much happier knowing that my system is running perfectly fine if not optimally :D

i know windows uses swap, but my main concern is when i used windows the harddrvie was ALWAYS reading or writing, and my ram would usually jump up to full n stuff quickly which is where my concern came from..

Thanks though, helped :D

---

### Post by VMC on 2008-07-15
By the way, typeing 'free' in a Terminal will also show swap usage. 

If you want to see if your swap works try burning a DVD using Brasero. 

It ate up 2gigs of ram and over 300mb of swap.

---

