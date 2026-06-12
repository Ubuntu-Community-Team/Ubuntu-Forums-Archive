---
title: "Unsafe Device Removal Work-around?"
date: 2008-03-28
forum: Hardware &amp; Laptops
---

### Post by noah420 on 2008-03-28
Okay,

after an extensive google search I have not found my answer

I used my slave drive on a windows machine i was working on, and just unplugged it (its a bad habit of mine, probably worse than my cigars =P) got it fixed, when I got home and went to use my drive, got the unable to mount volume because of unclean shutdown (i knew it would happen and meant to fix it before i gave the computer back) and now I do not have access to a windows machine to safely remove hardware, and cannot reinstall windows on my machine because the boot disk wont work for some reason

is there a workaround for this problem, I have tried to force the mount and got the error that '/dev/Slave Drive' is not recognized when I tried

sudo ntfs-3g -t '/dev/Slave Drive' '/media/Slave Drive' -o force

I am a totally lost linux newb

On an unrelated note

why wont the xp disk boot, I made a primary ntfs partition at the begining of the drive, is it because the ext3 partition is primary instead of logical? how can I change it to logical? I tried using GPartEd but did not see an option to change it to logical? if i could get windows re-installed I could fix it, but that is not working =(

I am so lost, picture me in the woods naked with no compass on 40 hits of acid... thats where im at right now

Thanks in advance

---

